---
title: "IS It posabal to install apache sql php on a usb drive?"
date: 2008-12-28
forum: General Help
---

### Post by JUSTINBEAIRD on 2008-12-28
IS It posabal to install apache sql php on a usb drive?


i dont have much space but i like to mess around with php sql part time 

is it poseabale to install it on a flash drive and mount and start it then remove it when its not needed so i dont hafto have it on the system all the time?

and if so how

i was using usbwebserver on windows

---

### Post by HermanAB on 2008-12-28
Yes, you can install an application anywhere you want.  There are a number of methods to do that.  You can tell the dpkg package manager to force the install to a specific path.  You can also install the program normally using synaptic, then copy it from /usr/wherever to wherever you want and make a soft link from the default path to the real path, so that it still appears to be at the original path, except that it actually isn't.

Hope that helps to get you going!

Herman

---

### Post by JUSTINBEAIRD on 2008-12-28
IS xampp that hard to instal on a usb ?

do i just hafto edit the shell script and how do i do that?

---

