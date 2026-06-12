---
title: "How to keep crebs from stretching my pictures"
date: 2013-09-06
forum: Desktop Environments
---

### Post by mbongiov on 2013-09-06
I am running crebs under Ubuntu 12.04 and the only complaint I have about it is that pictures that were taken in portrait format get stretched along their width in order to fit them to my 16:9 screen.  This usually results in only the top 1/3 of the picture being displayed.  Also, even pictures taken in landscape format are stretched slightly in order to fill the virtual space of my display as opposed to just the viewable part of my display.  Does anyone know of any ways to prevent the pictures from being stretched when they're displayed?

---

### Post by bkline on 2013-09-06
CREBS has several modes available for displaying the images.  Tile mode repeats the images across and down the display.  Zoom mode fills the screen without distortion, cropping if necessary.  Center ("Centre") mode does what it says, using the desktop background color if the image is smaller than the device resolution.  Scale mode is a compromise between centering and zooming, avoiding cropping or distortion.  Stretch mode forces the image dimensions to match the device resolution, distorting if necessary.  Span mode is like zoom for multiple monitors.  From your description it sounds like you're using Stretch mode, but you want Zoom or Scale.  For more information, take a look at the man page.

Good luck!

---

### Post by mbongiov on 2013-09-07
Okay, I found the style modes, but no matter what I do, it still stretches my pictures.  I looked at the xml file after changing the style and I don't see anything different as far as tags related to the style I've chosen.  Any idea how the style mode gets included in the xml file?

---

### Post by bkline on 2013-09-11
Check to make sure you haven't installed the software in such a way that ~/.crebs or its contents are not writable by the current user.

---

