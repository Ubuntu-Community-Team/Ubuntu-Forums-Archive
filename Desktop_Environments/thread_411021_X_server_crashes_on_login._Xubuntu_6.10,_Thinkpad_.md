---
title: "X server crashes on login. Xubuntu 6.10, Thinkpad T22."
date: 2007-04-16
forum: Desktop Environments
---

### Post by poscogrubb on 2007-04-16
Sometimes (not always) upon logging in to X, the screen changes to text mode, then back to graphics mode, then goes back to the login screen. Other times, login is successful and I get my XFCE desktop and apps. My /var/log/Xorg.0.log.old indicates that the X server crashed and provides the backtrace (see below). I'm using Xubuntu 6.10 installed on a Thinkpad T22. I believe it's using the S3 savage video driver?

tail of /var/log/Xorg.0.log.old:
```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions/libglx.so [0xb7bff946]
3: /usr/lib/xorg/modules/extensions/libglx.so(__glXleaveServer+0x22) [0xb7bdbc62]
4: /usr/lib/xorg/modules/extensions/libglx.so [0xb7bdc2fe]
5: /usr/bin/X(Dispatch+0x18f) [0x808693f]
6: /usr/bin/X(main+0x485) [0x806e715]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d218cc]
8: /usr/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

```

Relevant section of /etc/X11/xorg.conf:
```
Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "BusType" "PCI"
        Option          "DmaMode" "None"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C270-294 Savage/IX-MV"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection
```

What's going on, and how can I fix this? Let me know if there is some other information or files that would be helpful to know. Thanks!

---

### Post by lysergic on 2007-04-20
Hello there, have you had any luck sorting this problem out?? The reason your message caught my eye is because i am using an IBM Thinkpad T22 myself, and seem to have random troubles with the Xserver sometimes.. The last time it happened, X would just fail to load after boot, it would kinda flash [like it does when it normally boots up] but this time it just wouldnt load and just stayed black... i "sorted" this out, by running "dpkg-reconfigure xserver-xorg"  from the shell, after booting in "recovery mode" from the GRUB main menu.. Not to sure how i fixed it, or why it broke in the first place, but after seeing your post it makes  me wonder whether this could be a common fault for our model of laptops..

---

