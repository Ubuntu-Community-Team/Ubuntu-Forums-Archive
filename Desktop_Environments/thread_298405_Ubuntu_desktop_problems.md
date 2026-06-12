---
title: "Ubuntu desktop problems"
date: 2006-11-12
forum: Desktop Environments
---

### Post by mlazos on 2006-11-12
I'm new with Ubuntu and Linux and i messed up the desktop. Now every time i login i have only command line. Nothing graphical, all the commands work perfect but I'm still in Unix environment. Can someone please tell me how i can bring back the desktop and all the graphical interface?

---

### Post by pdub on 2006-11-12
You can try typing **startx**

Record any errors, if you get any, and post them back here.

---

### Post by mlazos on 2006-11-12
Here is the error message
------------------------------------------------------------------
(EE)Unable to find a valid framebuffer device
(EE)RADEON(0):Failed to open framebuffer device,consult warnings and/or errors above for possible reasons (you may have to see at the server log to see warnings).
(EE)RADEON(0):No valid modes found.
(EE)RADEON(0):RADEONFreescreen
(EE)Screen(s) found, but non of them have a usable configuration.
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server "0:0" after 0 requests (0 known processed) with 0 events remaining.
-----------------------------------------------------------------
Thanks alot for your help

---

### Post by pdub on 2006-11-12
Looks like you are having a problem with your video driver.

If you are running Ubuntu 6.10 Edgy then have a look at this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

If you are running Ubuntu 6.06 Dapper then look at this one:

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Follow the instructions for installing the ATI video drivers.

These guides are very good, especially for new users.

---

