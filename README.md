**Finding Lane Lines on the Road**
---
The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
---
## Reflection
---
### Description
---
The pipeline chosen contains in six steps:
- **grayAction**: Returns a gray scaled version of the input image using **cv2.cvtColor** OpenCv method.
- **blurAction**: Applies a Gaussian blur to the provided image using **cv2.GaussianBlur** OpenCV method.
- **cannyAction**: Use a [Canny transformation](https://en.wikipedia.org/wiki/Canny_edge_detector) to find edges on the image using **cv2.Canny** OpenCv method.
- **maskAction**: Eliminate parts of the image that are not interesting by defining the correct apex and applying **region_of_interest** helper function.
- **houghAction**: Use a [Hough transformation](https://en.wikipedia.org/wiki/Hough_transform) to find the lines on the masked image using **cv2.cv2.HoughLinesP** OpenCv method.
- **weightedAction**: Merges the output of **houghAction** with the original image to represent the lines on it using **weighted_img** helper function.
---
### Improvements
These were made to the **draw_lines** helper function in order to average and interpolate the lines going on the left and right side of the image by constantly monitoring the slope of the line. Each point of these lines was stored in a list and  the list passed to another helper function **draw_single_line** which gave the first degree polynomial using **numpy.polyfit** to match the line equation. When the line equation was found **y = mx +b** it was evaluated against the region of interest and also some correction factor.

---
## Potential shortcomings/suggestions
- The line size should be improved also the line gap.
- The frame rate of the videos I think is a bit high thus resulting in shaking lines when the images are overlapping
- The Hough parameters and choosing right kernel can give better results.
- Calculating the right region of interest was really time consuming and result in a lot of trials and errors until finding some region that worked.
- The videos sometimes cannot be seen from the notebook and some wrong MIME format appears as error message. They can be seen though from the output video folder.
