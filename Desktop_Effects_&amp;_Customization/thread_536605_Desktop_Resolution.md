---
title: "Desktop Resolution"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by weasel7711 on 2007-08-27
I feel like a blind person using this 1024x768 resolution with the enormous icons on my 20" monitor. However thats the highest it will go, how do I change that? I am running an NVIDIA Geforce 7600 512Mb edition with a dual core 1.8 Mhz Intel. Help...

---

### Post by smithman89 on 2007-08-27
I had this problem when i changed my monitor.  If you dont have it already, install nvidia-glx.  Then, run nvidia-settings in the terminal.  Click on "X Server Display Configuration".  There will be a dropdown menu for screen resolutions.  It will contain every possible resolution that your monitor can display (given that it detects the right monitor, if not, click detect displays).  Once you have done that, do the same thing for the root one; gksu nvidia-settings, type in password, change it the same way.  Then to check if the settings will stay, click quit, then ctrl+alt+backspace to restart the X server.

---

### Post by weasel7711 on 2007-08-27
> **smithman89 said:**
> I had this problem when i changed my monitor.  If you dont have it already, install nvidia-glx.  Then, run nvidia-settings in the terminal.  Click on "X Server Display Configuration".  There will be a dropdown menu for screen resolutions.  It will contain every possible resolution that your monitor can display (given that it detects the right monitor, if not, click detect displays).  Once you have done that, do the same thing for the root one; gksu nvidia-settings, type in password, change it the same way.  Then to check if the settings will stay, click quit, then ctrl+alt+backspace to restart the X server.

How do I install nvidia-glx? I have the nvidia accelerated graphics driver installed.. is that it?

---

### Post by weasel7711 on 2007-08-27
Oh ok nevermind i ran the settings in the terminal and that fixed it
thanks man
:guitar:

---

