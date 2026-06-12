---
title: "Problem with many open windows"
date: 2010-10-18
forum: Desktop Environments
---

### Post by Vik11 on 2010-10-18
Hello,
 
 I'm using Ubuntu 10.04. I enabled Compiz (I like it a lot), but when my Firefox is  starting and restoring previously open windows (a LOT of them with many  open tabs each, overall something like 20 windows and 70-80 tabs) at  some moment it stops rendering content of new windows and they appear as  "hang". If then later I disable Compiz, Firefox immediately renders all  of them just fine. If I restore Firefox at first and then enable  Compiz, then for some time all works fine, but then Firefox starts  scrolling very slow. If I suspend/resume the system, it becomes fast  again, but only for some time, then again become slow.
 
 At the  same time I noticed that as soon as Firefox hang restoring windows or  starts being slow Mplayer stops playing movies with messages "X11 error:  BadAlloc (insufficient resources for operation)". If I in Compiz  settings enable "Unredirect Fullscreen Windows" in fullscreen mode it  starts playing the movies again.
 
Could someone help me, please?
 
 1. Looks like Compiz hits some limit. Which? I guess, size of video memory?
 
 2. Can someone advise how it can be solved? Maybe, there is some knob I can tune?
 
 3.  If this is a video memory size limitation, how many memory do I need to  have it working? I'm going to upgrade my video card anyway.
 
 My system info:
 
 $ X -version
 
 X.Org X Server 1.7.6
 Release Date: 2010-03-17
 X Protocol Version 11, Revision 0
 Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
 Current Operating System: Linux ws 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686
 Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=5a45f345-e4be-5b7b-8c9b-2354df301a08 ro
 Build Date: 21 July 2010  12:47:34PM
 xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
 Current version of pixman: 0.16.4
     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
     to make sure that you have the latest version.
 
 3GB of system memory
 
 Video hardware NVidia GeForce 6800 Ultra with 256MB memory.
 
 xorg.conf:
 
 Section "Screen"
         Identifier      "Default Screen"
         DefaultDepth    24
 EndSection
 
 Section "Module"
         Load "glx"
         Load "dbe"
         Load "extmod"
 EndSection
 
 Section "Device"
         Identifier              "Default Device"
         Driver  "nvidia"
 
         Option "RandRRotation"  "on"
         Option "Coolbits"       "5"
         Option "DRI"            "True"
         Option  "metamodes"     "1280x1024_75 +0+0; nvidia-auto-select +0+0"
         Option  "NoLogo"        "True"
 EndSection
 
 NVidia driver version is 195.36.24
 
 I tried increasing PixmapCacheSize in 10MB (10 times from default) and set BackingStore to True, but those didn't help.
 
 Thanks,
 Vik

---

