---
title: "XFCE occasionally doesn't start"
date: 2013-08-12
forum: Desktop Environments
---

### Post by jonathan6 on 2013-08-12
Hi,

I've got a 9 year old laptop which I've recently installed Xubuntu 12.04 onto. Mostly it works very well, but occasionally, I turn it on and get left with a terminal prompt. I can log in, and the terminal is perfectly usable, but I'd rather have a GUI, and then start a terminal when I want one. I'm hoping someone here can help me.

When it happens, I tend to press Ctrl-Alt-Delete, it shuts down and reboots fine, and usually I get my GUI back (it has taken several reboots to achieve this on occasion). I've no idea if it's any different, but once I tried logging in and then using ```
sudo reboot
``` instead, and that rebooted into the terminal again, so I've tended to use Ctrl-Alt-Delete.

I don't really know how even start diagnosing/fixing this but I found some other threads where XFCE didn't load at all, and they suggested the ```
/var/log/Xorg.0.log
```, ```
/var/log/lightdm/lightdm.log
``` and ```
/var/log/lightdm/x-0.log
```, so I've attached copies from when it boots into GUI successfully, and when it doesn't. Although I can see failure messages in these, I'm not really sure how to proceed! The errors say it's unable to find a screen, although this is clearly only an intermittent problem.

Here are some excerpts from the logs (full versions, both for success and failure, attached):

x-0.log
```

DRM_IOCTL_I915_GEM_APERTURE failed: Bad file descriptor
Assuming 131072kB available aperture size.
May lead to reduced performance or incorrect rendering.
get chip id failed: -1 [9]
param: 4, val: 0


Fatal server error:
no screens found

```

lightdm.log
```

[+0.07s] DEBUG: Launching X Server[+0.07s] DEBUG: Launching process 972: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.07s] DEBUG: Waiting for ready signal from X server :0
[+0.07s] DEBUG: Stopping Plymouth, no displays replace it
[+3.45s] DEBUG: Process 972 exited with return value 1
[+3.45s] DEBUG: X server stopped
[+3.45s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+3.45s] DEBUG: Releasing VT 7
[+3.45s] DEBUG: Display server stopped

```

Xorg.0.log
```

[    24.404] drmGetBusid returned ''
[    24.404] (EE) intel(0): [drm] failed to set drm interface version.
[    24.404] (EE) intel(0): Failed to become DRM master.
[    24.404] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.404] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.404] (==) intel(0): RGB weight 888
[    24.404] (==) intel(0): Default visual is TrueColor
[    24.404] (II) intel(0): Integrated Graphics Chipset: Intel(R) 852GM/855GM
[    24.404] (--) intel(0): Chipset: "852GM/855GM"
[    24.404] (II) UnloadModule: "intel"
[    24.404] (II) Unloading intel
[    24.404] (EE) Screen(s) found, but none have a usable configuration.
[    24.404] 
Fatal server error:
[    24.404] no screens found
[    24.404] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    24.404] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    24.404] 
[    24.424]  ddxSigGiveUp: Closing log
[    24.424] Server terminated with error (1). Closing log file.

```

Can anyone advise me on what to do next; or, if I need to provide further information, what would be of use? If I have to just live with it that's fine, it's no more than a minor irritation at the moment. Since it is intermittent, is it a sign that my laptop's finally dying?

Many thanks!

Logs attached as bz2, as it didn't seem to want to let me attach them individually.
[ATTACH]245318[/ATTACH]

---

### Post by martinr on 2013-11-13
My reply was removed from this thread by a moderator.
Please see this [posting]("http://ubuntuforums.org/showthread.php?t=2187751&p=12847109#post12847109") for my similar if not the same problem.
I'm curious if you're also experiencing a frozen touchpad after a resume from suspend.

---

### Post by martinr on 2013-11-14
`

---

