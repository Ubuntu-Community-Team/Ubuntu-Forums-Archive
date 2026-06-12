---
title: "Logitech QuickCam help"
date: 2009-05-23
forum: General Help
---

### Post by optimsprm on 2009-05-23
I'm trying to get my Logitech QuickCam working on Jaunty, however whenever I try to run Camorama I get the error: "could not connect to video device (/dev/video0). Please check connection."

Anyone have any ideas on what I need to do? All the various things that I've tried have come up with a big fat score of: computer-1 Jason-0.

Thank you in advance.

---

### Post by jonathanku on 2009-05-25
I'm not running Camorama, but Ekiga gives a similar error. Skype / gstreamer-properties just hang when I try to test the video input.

I do have a /dev/video0 appear when I plug it in. Not sure if the webcam (2nd hand) is broken or not.

---

### Post by Wobblybob on 2009-05-25
Not running either of those progs but I'm using Cheese on jaunty Gnome desktop and it picks up my Logitech Quickcam E3500 series cam as a UVC Camera on /dev/video0/ straight out of the box.

---

### Post by HereInOz on 2009-05-25
Some Logitech QuickCams are not supported in Linux (the one I have, for instance - can't remember the model), so it is important to ensure that the camera is actually supported.

Check this list for QuickCams which are or are not supported.

[http://www.quickcamteam.net/devices/logitech_uvc_device_feature_list_by_device.pdf](http://www.quickcamteam.net/devices/logitech_uvc_device_feature_list_by_device.pdf)

---

### Post by jonathanku on 2009-05-25
Thanks for the list.

Any advice on how to determine the webcam model if I don't have the box etc?

Thanks.


p.s. "lsusb" might help, but it's returning nothing, and haning my terminal window.  :(   Something's up with my system.

---

### Post by jonathanku on 2009-05-26
OK - I've given up. I tried in a Windows machine and it wouldn't work either. There was maybe a good reason it was in the skip :o

-JK

p.s. sorry optimsprm for hijacking your thread.

---

