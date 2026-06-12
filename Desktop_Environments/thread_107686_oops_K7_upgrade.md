---
title: "oops K7 upgrade"
date: 2005-12-23
forum: Desktop Environments
---

### Post by Sp@z on 2005-12-23
I upgraded to the K7 kernel today and now when I restart the computer my screen gets all wonky. There is no text just different colored blocks and it won't reboot, I have to manually restart. Ut2K4 will not run, it simply crashes back to the desktop and UT99 says no glx found. I looked through Synaptic and I have glx installed (nvidea glx er something like that) I have the latest Nvidia drivers 8174. I tried rebooting into the 386 kernel and the same thing happens. Any help or suggestions would be appreciated! Thank you!

PS here is part of the error message. I would have put this in Gaming section, but to be honest it doesn't seem too many ppl game in linux. I more worried about the reboot hanging issue.

OpenGL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
appError called:
Couldn't set video mode: Couldn't find matching GLX visual

Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Executing USDLViewport::ShutdownAfterError
USDLGLRenderDevice::ShutdownAfterError
Signal: SIGIOT [iot trap]

---

### Post by Ampersand on 2005-12-23
Have you installed the linux-restricted-modules-k7 package?

---

### Post by Sp@z on 2005-12-23
Yes I have I dont have multiple CPU so I didnt install the K7 SMP..............

---

### Post by fordfan753 on 2005-12-23
Waaaaaaait a minute....the newest nvidia-glx in the Breezy repository is 7667, but you say you have 8174, which is the latest nvidia driver from the nvidia site. Then you go on to say that it's installed in synaptic....could it be possible that you installed 7667 from synaptic **and** 8174 from nvidia's website, making a horrible graphics conflict? Or am I just reading this wrong and your using Dapper sources or something?

---

### Post by Sp@z on 2005-12-24
fixed

---

