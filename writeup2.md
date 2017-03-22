
# **Finding Lane Lines on the Road** 

<!---
## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.



**Finding Lane Lines on the Road**
--->

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection
<!---
###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
--->
#### 1. Pipe Line Discription

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I apply Gaussian filter to blur the image to eliminate the noise in the image and use canny edge detector to detect the edge of a lane line. The parameter of the gaussian filter and canny detector has been tuned in order to keep the detected lane edge always available and in good condition. For next step, a mask of interst region is applied  to filt out objects which is not interested  in the image.  For the final step, I use Hough transform with a tuned parameters to find a lines in the image and draw red lines to mark out the lane line in the image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by devide lines detected by hough transform into 2 groups: Left_Lane_Lines and Right_Lane_Lines. In each group, the mean slope and the mean intercept point are calculate. A single  and solid line is drawn with these data.


<!---
If you'd like to include images to show how the pipeline works, here is how to include an image: 



< !  ![alt text][image1]>


###2. Identify potential shortcomings with your current pipeline
--->

#### 2. Potential Shortcomings with the pipeline

One potential shortcoming would be what would happen when the car drive through a shadow area. To overcome it, a HSV color transform is applied. By doing that, the detail of lane lines are preserved even when the car is driving through a shadow area.  

Another shortcoming is that when the lane line or the vehicle motion is changing rapidly, the detected lane line will also be not smooth and stable.

<!---
###3. Suggest possible improvements to your pipeline
--->

#### 3. Suggest Possible Improvement to the Pipeline

A possible improvement would be to use buffer to store detected lines information from the previous frames. By doing that, the drawn lane lines will be more stable.

Another potential improvement could be to apply kalmann filter to predict where the lane line will be. This will also improve the stability of the detected lane line.


```python

```
