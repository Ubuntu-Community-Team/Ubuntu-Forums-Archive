---
title: "X Server wont work, no errors. All distros made after June 06"
date: 2006-12-20
forum: Desktop Environments
---

### Post by EnforcerSG on 2006-12-20
Hi. I have been playing with Linux for about a year now and I like to try a lot of different distros but I always come back to Ubuntu just cause it works. Well, back in June when Ubuntu 6.06 came out I found when I booted from the live DVD and started it, after the status bar indicated that everything was done (mounting root file system, configuring stuff...) and it should have started X, my computer screen went black. Nothing happened after that; mouse and keyboard didn't work and it was just stuck.  No error messages, no nothing.  So after 10 minutes I restarted and tried it in graphics safe mode and it worked. Now I finally have a chance to install Ubuntu 6.10 (had to do a complete reinstall for other reasons) and even the safe mode it will lock up in the same way.

But I tried other distros that came out since then, Fedora 5, Knoppix 5.0, Mandriva 2007, Mepis 6, and they all have the same problem. Also if I can install the distro without using X, when it tries to run X after it finishes it will have the same problem.

If I can see what is going on (Knoppix) the last thing that will be displayed is "Starting the X windows system" before it goes black.

I thought that maybe it was the new kernel in all of those distros, 2.16.15 or higher, but right now I am using an old copy of Mepis 3.4.3 which according to distrowatch.com uses 2.16.15. Other old distros like Fedora 4, Ubuntu 5.10, and others still work without any problem.

I have used different CD/DVD burners and at different speeds. Some have even been cover disks from magazines, so I don't think it is a bad download or burned too fast.

Please help.

Hardware info:
Athlon 2500 XP
ABIT NS-7 motherboard
1024 Meg Ram
ATI Radion X800 Pro
Creative Labs SB Audigy 2 ZS

Please help. If you need more info let me know. If "left"grading to a new nVidia video card would help I will consider it (not too many AGP video cards in my price range that are clearly faster than what I have now, so it wouldn't be an upgrade, and I won't downgrade, so leftgrade). The ATI drivers are a ***** anyway.

---

### Post by acturneruk on 2006-12-20
I have an X700 ATI card, and have experienced the same problems as you regarding the 6.06 and 6.10 live CDs/DVDs. I installed using the alternate text-based installer CD, and then booted into recovery mode and add the following line to my "Device" section in xorg.conf:-

```
Option	    "MonitorLayout" "LVDS, AUTO"
```

and changed:-

```
Driver      "ati"
```

to:-

```
Driver      "radeon"
```

Then rebooted, and everything works. I had to do the same thing on my Gentoo box to get X to work. Hopefully this will work for you too.

Oh, and can you Ctrl-Alt-Fx to a console?

---

### Post by EnforcerSG on 2006-12-20
I did exactly what you said and it didn't work.  But someone told me that whatever the DRI is might be causing it so I commented out everything with DRI from xorg.conf and X works.  I am stuck at 640x480 resolution right now but I am working on installing the proprietary ATI driver now so hopefully Ubuntu 6.10 will work.

Ctrl-Alt-F[1-12] did not work at all when it locked up.

I seem to have a work around now, but if anyone else has any information about this bug please let me know.

---

