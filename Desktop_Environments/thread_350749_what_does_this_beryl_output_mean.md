---
title: "what does this beryl output mean?"
date: 2007-02-01
forum: Desktop Environments
---

### Post by fiveryanfrenzy on 2007-02-01
> :~$ beryl-manager
:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

Help?

---

### Post by allwin on 2007-02-01
Look over these instructions.  Make sure your xorg.conf contains the DRI and Mode 0666 lines and composite extension!

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

A lot depends upon what kind of video card you have and what driver you have installed.  Not all combinations work.  The above guide helps sort that out.  You can TRY other things, but most often will end up no better off than you are now!  Hope that helps.

---

