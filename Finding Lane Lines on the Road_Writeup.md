# Finding Lane Lines on the Road

---
**Finding Lane Lines on the Road**
The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---
### Reflection

### 1. Description of pipeline

At first, I read the images from the *test_images* folder using a **for()** loop. Then the image processing consisted of 5 steps. The first thing is converting the image to gray scale by *cv2.covCOLOR* function. Next, I applied Gaussian smoothing followed by the Canny transform for edges detection. Then I created a mask that indicated the region of interest and combined the mask and the edge image. Finally, I created the Hough lines on the masked image. This part is the key point of this pipeline. To gain a single line for each lane, I modified the *draw_lines()* function as following. In the line loop, I first separate the line segments to left lane and right lane by their slope, i.e. left lane for positive slope and right lane for negative slope. Actually, I set a threshold of slope for separating the line sigments in order to avoid unnecessary noise. Then I calculated the average value of the segment and the slope for both categories of lines. Using these average values, I drawed a single line to represent the actual lane for both sides.

Here are two examples of using the line segment and single line to represent the lane
![line segment](/test_images_output/image1.jpg)
![single line](/test_images_output/image_final1.jpg)

### 2. Potential shortcomings with the pipeline

One potential shortcoming could be the fixed region of interest. If the car change lane or not run in the middle of the lane, the pipeline could not get the right region of interest and then fail to detect the lane.

Another shortcoming could be the straight line that I used to represent the lane. If the road is curve, the straignt line would unable to indicate the lane properly.

### 3. Suggest possible improvements

The possible improvement would be using a more robust fitting method to represent the lane rather than a straignt line. And try to design a more flexible region of interest instead of this fixed one.
