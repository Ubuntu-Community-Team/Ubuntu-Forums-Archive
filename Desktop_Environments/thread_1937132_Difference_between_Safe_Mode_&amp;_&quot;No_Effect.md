---
title: "Difference between Safe Mode &amp; &quot;No Effects&quot; ??"
date: 2012-03-07
forum: Desktop Environments
---

### Post by dave2001 on 2012-03-07
I'm trying to troubleshoot a graphics problem. After a recent update and reboot, I was met with a black screen.

I've worked through the problem some, now I can get to the login screen normally. However, Safe Mode is the only session that works, and knowing why might help me figure out what else I need to do.

I'm wondering what exactly the differences are between "safe mode" and the classic desktop "no effects" mode? 

Thanks for any information!

---

### Post by jerrrys on 2012-03-07
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=recovery+mode&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=recovery+mode&sa=Search&cof=FORID:9)

Gnome-classic no-effects.  Is the Gnome-classic desktop environment without compiz.  Also known as gnome-fallback.

---

### Post by dave2001 on 2012-03-07
Thanks for the reply jerrrys!

I wasn't referring to "recovery mode", which is reached through the grub menu. I'm talking about one of the options available as a session at the login screen of 11.04. It is called "Ubuntu (safe mode)".

I'm trying to determine why my system will load the desktop correctly when in "safe mode" session, but not in a "no effects" session. If compiz is already disabled in "no effects" what else would be causing this difference?

---

### Post by 3Miro on 2012-03-07
Check the graphical driver. "Safe Mode" disables the effects, but it also disables any drivers that can cause trouble. When you see problems on Linux, it is usually due to a graphical driver.

If you are using proprietary Nvidia or ATI drivers, you should go into "Safe Mode" uninstall the driver, reboot, reinstall the driver and reboot again. This usually solves the problem.

Every time there is a kernel update, the proprietary driver has to update as well. This should happen automatically, but every now and then we see people here where that fails. Reinstalling the driver usually works.

---

### Post by dave2001 on 2012-03-08
Thanks for the suggestion 3Miro!

Before all this trouble began I was indeed using proprietary nvidia drivers for my nvidia 8400GS card. 
In the beginning I had a black screen after grub loaded. Purging the nvidia drivers from the system via recovery tty prompt enabled me to get a normal login screen. Still only loads the desktop in safe-mode though. All other sessions produce a desktop with no icons, no panels, and no keyboard response (except to ctrl+alt+bcksp and the RSEIUB sequence).

So I'm pretty sure the system is already just using the generic nvidia driver. I tried to reinstall the proprietary one using the gui utility while in safe mode, but it gave me an "unauthorized" message. I'll try reinstalling using apt-get and see if that helps.

---

### Post by 3Miro on 2012-03-08
If you know how to re-install the Nvidia driver from apt-get, then it is OK. I personally don't know how to do it.

If you want to know if you are running the nvidia driver, go to terminal and type:
```
sudo lsmod
```
and look for "nvidia". You can also let it look for you with
```
sudo lsmod | grep nvidia
```
The proprietorial driver is called "nvidia", the default one is called "noveau".

You can also use the Nvidia settings utility, it will complain if you are not running the Nvidia driver.

---

### Post by dave2001 on 2012-03-08
Thanks for the suggestion to try reinstalling the graphics driver 3Miro! Problem sovled! 

I reinstalled the nvidia proprietary driver via the terminal since the gui driver-installation utility wasn't working in safe mode. 
In case anyone else reading here needs it, this is command:
 ```
~$ sudo apt-get install nvidia-current 
```Everything is now working flawlessly again, including a self-compiled version of emerald window decorator. I'm not sure why the nouveou driver was causing such a mess.

The "additional drivers" gui utility shows the nvidia driver as "not currently in use" but according to terminal output on lshw and lsmod, it IS in use. So I'm guessing this is another bug in the gui utility.

---

### Post by grahammechanical on 2012-03-08
I am guessing that safe mode is a low resolution mode that will not break your monitor by running it at too high a resolution and refresh rate.

It gives you a graphical user interface which you can use to fix the problem.

This is different from Classic mode without effects. In classic mode the video driver should still be running the monitor at the optimum settings. It is just that the video card does not have enough of its own memory and/or a powerful enough GPU to give special or 3D effects.

We can get put into safe mode at boot up when the X-server fails to work out the optimum setting for the monitor. I had this happen to me when the video card was overheating and starting to fail.

Regards.

---

