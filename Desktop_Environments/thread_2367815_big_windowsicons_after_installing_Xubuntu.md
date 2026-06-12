---
title: "big windows/icons after installing Xubuntu"
date: 2017-08-03
forum: Desktop Environments
---

### Post by shakkaar on 2017-08-03
Hello everyone. I installed Xubuntu 32 in an old laptop but the windows and icons look big, way ? see this photo : [https://goo.gl/photos/cLDAWxi3X8xGfFPq7](https://goo.gl/photos/cLDAWxi3X8xGfFPq7)

---

### Post by Dennis N on 2017-08-03
Desktop Icons have a size setting in: Menu > Settings > Desktop > Icons.

---

### Post by shakkaar on 2017-08-03
Thank you, I found Windows settings too, but I didn't find how to reduce the size
[https://goo.gl/photos/9etPjNWUGDBfSxCX7](https://goo.gl/photos/9etPjNWUGDBfSxCX7)    [https://goo.gl/photos/Cx4hbRSVLWfYxAYY9](https://goo.gl/photos/Cx4hbRSVLWfYxAYY9)

---

### Post by ajgreeny on 2017-08-03
What resolution is the machine giving you and what video hardware have you got?  Perhaps you need to try to use a higher resolution for the display.
Go to **Display** in the hardware section of Settings to see what resolution you are using now; for video hardware use command **lspci** in terminal.

---

### Post by grahammechanical on 2017-08-03
If it is an old machine it may be loading in low resolution mode because a proprietary video driver has not been found for that video card. When you installed, did you tick the box Install third party software? That will install not only some third party/proprietary audio and visual codecs but also a proprietary video driver. And one might not be available for that hardware. Hence, the switch to a low resolution mode.

Somewhere on Xubuntu there should be a utility called Additional Drivers. That will offer you a selection of open source and proprietary video drivers. You need to be connected to the internet and allow time for the utility to do its stuff.

Regards

---

### Post by Dennis N on 2017-08-03
> **shakkaar said:**
> I didn't find how to reduce the size

Settings > Desktop > Icons:

---

### Post by shakkaar on 2017-08-09
Sorry for being late. thank you so much for your responses 
@Dennis I changed the size of  desktop icons but the windows can't be reduced
@Ajegreeny this is the resolution from the display window 640x480 [https://goo.gl/photos/XAUe9FRdQR8igBFb8](https://goo.gl/photos/XAUe9FRdQR8igBFb8)   that can't be possible ? I installed Xubuntu in a second old Laptop  "msi" and it worked very good here the display window 1280x800 with the  possiblity to change it [https://goo.gl/photos/KG31a2EdyHoyoyWF9](https://goo.gl/photos/KG31a2EdyHoyoyWF9) unlike the first laptop
@grahammechanical : Yes I  ticked the box Install third party software. this is the additional drivers window [https://goo.gl/photos/oZsauYU26rpeJLxF9](https://goo.gl/photos/oZsauYU26rpeJLxF9)    I ticked the first option "using processor micro,,," but still the problem exist,

---

### Post by vasa1 on 2017-08-09
Can't you just take a screenshot instead of posting images of your laptop? And you can upload images here itself by using the forum's attachment facility: just click on the paper-clip icon. If you don't see that icon, click on "Go Advanced" first.

---

### Post by shakkaar on 2017-08-10
@vasa1 ; Thank you :) but I guess taking a picture with phone + the google  photo link on my main laptop is easier than taking a screenshot in a  laptop that is not working good and register my password and username of  the forum on it browser,

---

