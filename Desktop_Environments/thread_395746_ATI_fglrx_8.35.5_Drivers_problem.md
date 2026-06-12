---
title: "ATI fglrx 8.35.5 Drivers problem"
date: 2007-03-28
forum: Desktop Environments
---

### Post by jackkerouac on 2007-03-28
I guess not a large problem.

I installed the AMD/ATI 8.35.5 fglrx drivers and everything went fine, but I cannot open their (admittedly experimental) Catalyst Control Center for Linux.

I get the following error when trying to open it:

```
*** glibc detected *** amdcccle: munmap_chunk(): invalid pointer: 0xbfa5ea53 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb7b94b4a]
amdcccle[0x85a5317]
amdcccle(AtiXUPcs_GetVal+0x68)[0x85a5178]
amdcccle(AtiXUDisp_InitContext+0x85)[0x85a3645]
amdcccle(AtiXUPriv_InitContext+0x4f)[0x85a26df]
amdcccle(__AtiXUtil_Open+0x9b)[0x85a154b]
amdcccle(main+0x106)[0x81449b6]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7b438cc]
amdcccle[0x8142d21]
======= Memory map: ========
08048000-0869e000 r-xp 00000000 03:41 6193292    /usr/bin/amdcccle
0869e000-08754000 rwxp 00656000 03:41 6193292    /usr/bin/amdcccle
08754000-089d0000 rwxp 08754000 00:00 0          [heap]
b79e0000-b79e1000 r-xp 00000000 03:41 6490498    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b79e1000-b79e2000 rwxp 00000000 03:41 6490498    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b79e2000-b7a15000 r-xp 00000000 03:41 6686441    /usr/lib/locale/en_CA.utf8/LC_CTYPE
b7a15000-b7aec000 r-xp 00000000 03:41 6686464    /usr/lib/locale/en_CA.utf8/LC_COLLATE
b7aec000-b7aee000 rwxp b7aec000 00:00 0 
b7aee000-b7af2000 r-xp 00000000 03:41 6195801    /usr/lib/libXfixes.so.3.1.0
b7af2000-b7af3000 rwxp 00003000 03:41 6195801    /usr/lib/libXfixes.so.3.1.0
b7af3000-b7af4000 rwxp b7af3000 00:00 0 
b7af4000-b7b10000 r-xp 00000000 03:41 6194297    /usr/lib/libexpat.so.1.0.0
b7b10000-b7b12000 rwxp 0001c000 03:41 6194297    /usr/lib/libexpat.so.1.0.0
b7b12000-b7b25000 r-xp 00000000 03:41 1589732    /usr/lib/libz.so.1.2.3
b7b25000-b7b26000 rwxp 00012000 03:41 1589732    /usr/lib/libz.so.1.2.3
b7b26000-b7b2a000 r-xp 00000000 03:41 1589717    /usr/lib/libXdmcp.so.6.0.0
b7b2a000-b7b2b000 rwxp 00003000 03:41 1589717    /usr/lib/libXdmcp.so.6.0.0
b7b2b000-b7b2d000 r-xp 00000000 03:41 1589713    /usr/lib/libXau.so.6.0.0
b7b2d000-b7b2e000 rwxp 00001000 03:41 1589713    /usr/lib/libXau.so.6.0.0
b7b2e000-b7c5b000 r-xp 00000000 03:41 29361521   /lib/tls/i686/cmov/libc-2.4.so
b7c5b000-b7c5d000 r-xp 0012c000 03:41 29361521   /lib/tls/i686/cmov/libc-2.4.so
b7c5d000-b7c5f000 rwxp 0012e000 03:41 29361521   /lib/tls/i686/cmov/libc-2.4.so
b7c5f000-b7c62000 rwxp b7c5f000 00:00 0 
b7c62000-b7c6c000 r-xp 00000000 03:41 29327384   /lib/libgcc_s.so.1
b7c6c000-b7c6d000 rwxp 00009000 03:41 29327384   /lib/libgcc_s.so.1
b7c6d000-b7c6e000 rwxp b7c6d000 00:00 0 
b7c6e000-b7c92000 r-xp 00000000 03:41 29361529   /lib/tls/i686/cmov/libm-2.4.so
b7c92000-b7c94000 rwxp 00023000 03:41 29361529   /lib/tls/i686/cmov/libm-2.4.so
b7c94000-b7d44000 r-xp 00000000 03:41 6196131    /usr/lib/libstdc++.so.5.0.7
b7d44000-b7d49000 rwxp 000af000 03:41 6196131    /usr/lib/libstdc++.so.5.0.7
b7d49000-b7d4e000 rwxp b7d49000 00:00 0 
b7d4e000-b7de6000 r-xp 00000000 03:41 6195420    /usr/lib/libGL.so.1.2
b7de6000-b7deb000 rwxp 00098000 03:41 6195420    /usr/lib/libGL.so.1.2
b7deb000-b7dee000 rwxp b7deb000 00:00 0 
b7dee000-b7df5000 r-xp 00000000 03:41 1589729    /usr/lib/libXi.so.6.0.0
b7df5000-b7df6000 rwxp 00006000 03:41 1589729    /usr/lib/libXi.so.6.0.0
b7df6000-b7e05000 r-xp 00000000 03:41 29361549   /lib/tls/i686/cmov/libpthread-2.4.so
b7e05000-b7e07000 rwxp 0000f000 03:41 29361549   /lib/tls/i686/cmov/libpthread-2.4.so
b7e07000-b7e09000 rwxp b7e07000 00:00 0 
b7e09000-b7e11000 r-xp 00000000 03:41 6195735    /usr/lib/libXcursor.so.1.0.2
b7e11000-b7e12000 rwxp 00007000 03:41 6195735    /usr/lib/libXcursor.so.1.0.2
b7e12000-b7e13000 rwxp b7e12000 00:00 0 
b7e13000-b7e7c000 r-xp 00000000 03:41 6195066    /usr/lib/libfreetype.so.6.3.12
b7e7c000-b7e80000 rwxp 00068000 03:41 6195066    /usr/lib/libfreetype.so.6.3.12
b7e80000-b7e82000 r-xp 00000000 03:41 6194271    /usr/lib/libXrandr.so.2.0.0
b7e82000-b7e83000 rwxp 00002000 03:41 6194271    /usr/lib/libXrandr.so.2.0.0
b7e83000-b7e8a000 r-xp 00000000 03:41 6194250    /usr/lib/libXrender.so.1.3.0
b7e8a000-b7e8b000 rwxp 00006000 03:41 6194250    /usr/lib/libXrender.so.1.3.0
b7e8b000-b7eb4000 r-xp 00000000 03:41 6193803    /usr/lib/libfontconfig.so.1.0.4
b7eb4000-b7eb9000 rwxp 00028000 03:41 6193803    /usr/lib/libfontconfig.so.1.0.4
b7eb9000-b7eba000 rwxp b7eb9000 00:00 0 
b7eba000-b7f80000 r-xp 00000000 03:41 1589725    /usr/lib/libX11.so.6.2.0
b7f80000-b7f83000 rwxp 000c5000 03:41 1589725    /usr/lib/libX11.so.6.2.0
b7f83000-b7f8f000 r-xp 00000000 03:41 1589721    /usr/lib/libXext.so.6.4.0
b7f8f000-b7f90000 rwxp 0000c000 03:41 1589721    /usr/lib/libXext.so.6.4.0
b7f90000-b7f91000 rwxp b7f90000 00:00 0 
b7f91000-b7f93000 r-xp 00000000 03:41 29361527   /lib/tls/i686/cmov/libdl-2.4.so
b7f93000-b7f95000 rwxp 00001000 03:41 29361527   /lib/tls/i686/cmov/libdl-2.4.so
b7f9f000-b7fa0000 r-xp 00000000 03:41 6686442    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
b7fa0000-b7fa1000 r-xp 00000000 03:41 6686463    /usr/lib/locale/en_CA.utf8/LC_TIME
b7fa1000-b7fa2000 r-xp 00000000 03:41 6686465    /usr/lib/locale/en_CA.utf8/LC_MONETARY
b7fa2000-b7fa3000 r-xp 00000000 03:41 6686467    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fa3000-b7fa4000 r-xp 00000000 03:41 6686468    /usr/lib/locale/en_CA.utf8/LC_PAPER
b7fa4000-b7fa5000 r-xp 00000000 03:41 6686449    /usr/lib/locale/en_CA.utf8/LC_NAME
b7fa5000-b7fa6000 r-xp 00000000 03:41 6686469    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
b7fa6000-b7fa7000 r-xp 00000000 03:41 6686470    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
b7fa7000-b7fa8000 r-xp 00000000 03:41 6686452    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
b7fa8000-b7faf000 r-xs 00000000 03:41 6209979    /usr/lib/gconv/gconv-modules.cache
b7faf000-b7fb0000 r-xp 00000000 03:41 6686471    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
b7fb0000-b7fb8000 r-xp 00000000 03:41 6193911    /usr/lib/libSM.so.6.0.0
b7fb8000-b7fb9000 rwxp 00007000 03:41 6193911    /usr/lib/libSM.so.6.0.0
b7fb9000-b7fce000 r-xp 00000000 03:41 6193900    /usr/lib/libICE.so.6.3.0
b7fce000-b7fcf000 rwxp 00014000 03:41 6193900    /usr/lib/libICE.so.6.3.0
b7fcf000-b7fd3000 rwxp b7fcf000 00:00 0 
b7fd3000-b7fec000 r-xp 00000000 03:41 29327562   /lib/ld-2.4.so
b7fec000-b7fee000 rwxp 00018000 03:41 29327562   /lib/ld-2.4.so
bfa4a000-bfa5f000 rwxp bfa4a000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

I'm just curious if anyone else has had this problem and if there is any solution for it.

---

### Post by mintcoffee on 2007-03-28
Yup.. getting the same problem. I just installed the 8.35.5 drivers in Edgy. It's too bad, I was hoping for a good GUI to control some of the aticonfig functions.

---

### Post by Toolbelt on 2007-03-28
Same here.....with Feisty.....so I guess if mintcoffee is running on 2.6.18 kernel that the 2.6.20 kernel patch I had to do to get 8.35.5 to run on Feisty is not the source of the problem....

---

### Post by WarpFactor10 on 2007-03-29
Same deal with me as well with a ATI 200M in Fiesty. 
I used the ATI Wiki to get it running [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

I ended up having to use the second script to get it running on my install. Everything else works perfectly fine, Video playback and it uses the correct driver for display and everything in fglrxinfo.  For fun I tried remove the amdcccp and putting in the old control control center from the last release and that either doesn't work with the new driver set, or has the same problem, as it doesn't open either and just crashes.

---

### Post by jackkerouac on 2007-03-29
Okay, got it working, sort of.

All I did was boot into Ubuntu using regular Gnome, no XGL. The Catalyst Control Center (amdcccle) pops up and runs no problem.

---

### Post by WarpFactor10 on 2007-03-30
> **jackkerouac said:**
> Okay, got it working, sort of.

All I did was boot into Ubuntu using regular Gnome, no XGL. The Catalyst Control Center (amdcccle) pops up and runs no problem.

How'd you manage to do that? I figure it's some setting in xorg.config, just not sure which one. I'm using KDE too, but I guess it should be the same if it's just in xorg.conf.  What cards are you guys running? I have a Express 1150 / 200M on my MSI-1058 notebook. Also, a problem that disapeared in the last release, no video and lockup when you log out, seems to have come back...

---

### Post by scott_evil on 2007-03-30
> **WarpFactor10 said:**
> How'd you manage to do that? I figure it's some setting in xorg.config, just not sure which one. I'm using KDE too, but I guess it should be the same if it's just in xorg.conf.  What cards are you guys running? I have a Express 1150 / 200M on my MSI-1058 notebook. Also, a problem that disapeared in the last release, no video and lockup when you log out, seems to have come back...

I have the same problem, but I'm not giving up my Beryl :)

To get to the Gnome session just CTRL-ALT-Backspace to go to the login screen and change the session default with the Options in the lower lefthand corner of the screen.

*Warning* this will log you out of your current session and close all open windows and programs.

If you just want to see what you're missing you can look [here](http://www.michaellarabel.com/index.php?k=blog&i=135).

---

### Post by WarpFactor10 on 2007-04-02
Last night for fun I ended up reformating my laptop, and reinstalling Fiesty x64 from scratch. (I was ununtu Edgy x86 and just updated to Fiesty before...)
Everything went fine, except I had to run aticonfig --initial and aticonfig --overlay-type=Xv after shutting X server down for some reason, I got errors otherwise.

Now I get a different problem. Rather than running and just crashing, the new ATI Catylist Control Center wont install. i went through and the .deb that was genorated is installed correctly..and the amdccc or whatever binary was in /usr/bin..... but when I tried to run the command,  I get command not found. :confused: 
I even extracted the .deb manually and tried running them right from the folder, same problem. Really weird. Maybe x64 support for CCC isn't ready yet? (That is if you considor the x86 ready even...)

---

### Post by chris_c28 on 2007-04-04
It's because we're running on Display 1 using Beryl. Similar to how we run aticonfig from Beryl, you have to do "DISPLAY=:0 amdcccle" from terminal to launch the control panel.

---

### Post by WarpFactor10 on 2007-04-04
> **chris_c28 said:**
> It's because we're running on Display 1 using Beryl. Similar to how we run aticonfig from Beryl, you have to do "DISPLAY=:0 amdcccle" from terminal to launch the control panel.

Thanks! Works perfect!

---

### Post by HellishER on 2007-04-12
Hello, followed a guide somewhere here and got the drivers installed and working.
Im using ubuntu 6.10 64bits.
But the amdcccle cant be run, if i trying the shortcut in the menu it say it cant find amdcccle.

I have located the file in usr/bin/, but not sure if its a executable or not, cant runt i from terminal either.
hell@hell:/usr/bin$ ./amdcccle
bash: ./amdcccle: No such file or directory

Im new to linux and i can clearly see the file in that folder, but it wont run/find it..

Edit: Nevermind, the file was gone after some reboots..

---

### Post by melk on 2007-04-20
I get the crash at aticonfig --initial so my xorg.conf isn't even configured for my card :/  Starting to wonder if the X1950 are really *not* supported (although it worked with 6.10 x32)

Tried and still searching for a way to configure my xorg.conf.  worst comes to worst, I'll use the Method 1 [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

and see it it fixes my problems and retry method 2 without needing aticonfig

Anyhow, glad you were able to get the ccc working :)

M

---

### Post by dejitarob on 2007-04-20
Aticonfig crashes for me too on the 8.36.5 drivers. Doing a 'aticonfig --initial --force' fixed it, but I still get it if I try to do an 'aticonfig --overlay-type=Xv'.

---

