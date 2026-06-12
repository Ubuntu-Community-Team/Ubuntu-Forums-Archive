---
title: "help cant run steam on Ubuntu 18.04 libGL error: unable to load driver: radeonsi_dri."
date: 2018-04-29
forum: Gaming &amp; Leisure
---

### Post by jcer93705 on 2018-04-29
Trying to run steam but it say. This message. Can someone get my steam running. I'm running Ubuntu 18.04 on built in driver. I'm using Rx 480

$ steam
Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by i7Fd-2sCB1 on 2018-04-29
> **jcer93705 said:**
> Trying to run steam but it say. This message. Can someone get my steam running. I'm running Ubuntu 18.04 on built in driver. I'm using Rx 480

$ steam
Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
ERROR: ld.so: object 'libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

It works for me when I used AMD Radeon graphics card the R7 370 version and it loads without any issues. What's bugs me is why have you got it running from terminal? Does the shortcut launcher not work from the "show applications" menu from dock? Also have you got xorg.conf configured on my system I ran it without any xorg.conf file installed.

---

### Post by jcer93705 on 2018-04-30
> **centralpython said:**
> It works for me when I used AMD Radeon graphics card the R7 370 version and it loads without any issues. What's bugs me is why have you got it running from terminal? Does the shortcut launcher not work from the "show applications" menu from dock? Also have you got xorg.conf configured on my system I ran it without any xorg.conf file installed.

I launch it from terminal everyone can see the error. When I simply click on steam nothing happens. I didn't do nothing to xorg.conf.

---

### Post by justausername on 2018-05-02
Hi, I had the same problem with my setup.
I was able to fix it by installing and running this Tool: [https://github.com/drakofrost/steam-launcher](https://github.com/drakofrost/steam-launcher)

Just install it by following the guide, then run it from the starter and select patch Steam runtime.

---

### Post by joyjeetchowdhury-gmail on 2018-05-06
Thanks for your suggestion, this is a perfect solution, after patching, Steam started working.


> **justausername said:**
> Hi, I had the same problem with my setup.
I was able to fix it by installing and running this Tool: [https://github.com/drakofrost/steam-launcher](https://github.com/drakofrost/steam-launcher)

Just install it by following the guide, then run it from the starter and select patch Steam runtime.

---

### Post by el_heffe on 2018-06-10
Just FYI for those coming here trying to get Steam working on Ubuntu 18.04 like I did and finding the above link not working because the original author pulled their code after Microsoft bought Github.  I have forked the code from the below link (my repo linked below), but this is what I did in the meantime:
```

$ wget https://raw.githubusercontent.com/digideskio/steam-launcher/master/steam-launcher.sh
$ chmod +x steam-launcher.sh
$ ./steam-launcher.sh

```
[IMG]https://github.com/elheffe80/steam-launcher/raw/master/screenshot.png[/IMG]
Then, at the window that was launched and is seen above, I selected Patch Steam Runtime, and because I was running it for the first time, it installed no problem. 
 Furthermore, I ran it from the default launcher, and it launched no problem from then on.  Note that I did not feel the need to full on install it, nor to pull the full repo in order to do so, and haven't had any issues.
Also, if you feel the need to, or the above link no longer works, here is my repo on github (I am not a maintainer, but will do what I can if needed/possible): [https://github.com/elheffe80/steam-launcher](https://github.com/elheffe80/steam-launcher)

---

### Post by johnnwfs on 2018-07-14
Worked like a charm el_heffe. Thanks a million! --John

---

### Post by letatcest on 2018-08-10
[SIZE=2]I've been trying to get Steam working with my AMD Radeon RX 560 card ever since I upgraded from 16.04 to 18.04. But I never got it working. When I remove the card and use the onboard Intel video card (HD530 I believe, it's an Intel Skylake i5), Steam runs (but not so good for demanding games of course!). 

I tried removing files, renaming files, deleting everything, installing the AMD drivers from the website. But the often mentioned message never goes away:

Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Installing breakpad exception handler for appid(steam)/version(1533766730)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast


Also tried the Steam Launcher script (it was the latest possible option I found), but no difference either way.

Is there any other option? (except for reinstalling the system completely, which I rather not do)

[SIZE=3]Update: I re-installed the system and no errors anymore. I don't like the fact that I could not find out what was actually wrong, but this seems a workable solution (and a clean system is not so bad either)[/SIZE][/SIZE]

---

