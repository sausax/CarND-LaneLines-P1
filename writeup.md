# **Finding Lane Lines on the Road** 

## Writeup Template

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./pipeline_images/gray.jpg "Grayscale"
[image2]: ./pipeline_images/blur.jpg "Gaussian Blur"
[image3]: ./pipeline_images/edges.jpg "Canny Edges"
[image4]: ./pipeline_images/masked.jpg "Masked region of interest"
[image5]: ./pipeline_images/lines.jpg "Hough lines"
[image6]: ./pipeline_images/final.jpg "Final image"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
### 1. Pipeline description

My pipeline consisted of 5 steps.
First, I converted the images to grayscale

![alt_text][image1]

After that I added gaussian blur to the image

![alt_text][image2]

Next I ran Canny edge detection to detect edges. 

![alt_text][image3]

Then I added a masked to select the region of interest (ROI)
I used a quadilateral mask for this task

![alt_text][image4]

Next I applied Hough transform to masked image with lane lines

![alt_text][image5]

Finally, I added marked lanes over the original image

![alt_text][image6]

### 2. Draw line function

In draw_lines() function I did the following modifications

First, I iterate over all lines and divided them into right and left lines.
All lines that have slope between 0.48 and 0.70 were classified as left lane line and lines that
have slope between -0.85 and 0.63 were classified as right lane line.

After that I calculated average slope and intercept for right and left lane line. 

Next I calculated the start and end point of lane lines using y_max = image.shape[0] and y_min = 320. 

Finally, I added lane lines over the image. 


### 3. Potential shortcomings

One shortcoming is that I am hardcoding the qudilateral vertices in the code. This can be a problem when size of the image changes or camera angle changes.

Another problem is that the code breaks when encountering curved road.


### 4. Possible improvements

*Ability to dynamically select region of interest.
*Better tuned parameters for Hough transform. 
*Non linear line fitting.


