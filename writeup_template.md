# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # "Image References"

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 7 steps.

1. Call grayscale to converted the images to grayscale 

   ![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\step1.png)

2. Call gaussian_blur to suppress noise and spurious gradients by averaging with kernel_size = 5

   ![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\step2.png)

3. Call canny to detect edges with low_threshold = 50 and high_threshold = 150

   ![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\step3.png)

4. Call region_of_interest to filter edges in a reasonable region

   ![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\step4.png)

5. Call hough_lines to get lines of the lane boundaries

   ![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\step5.png)

6. Call dstack to convert edges to a color image

7. Call weighted_img to blend the image made by colored lines of lane boundaries and original image

   ![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\step6.png)



Tuning parameters  is a main work.  The function region_of_interest to clip a region of target, it's parameters effect the counter of the chosen edges, and the parameters of the function hough_lines also effect the result of detected lines of lane boundaries. The first image is original image, and the second image is the image after tunning parameters.  

![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\5_before.png)

![](D:\hzf\udacity\project\CarND-LaneLines-P1-master\test_images_output\5_after.png)

  


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be loss some edges where the road is curve and the front party of the roads is outside the critical area.




### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make a series of segments into a link.
