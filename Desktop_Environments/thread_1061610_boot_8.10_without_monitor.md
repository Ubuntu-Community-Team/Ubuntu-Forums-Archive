---
title: "boot 8.10 without monitor"
date: 2009-02-06
forum: Desktop Environments
---

### Post by airzoink on 2009-02-06
hello guys! got this error going everytime i start my box without a monitor it gives an error "no screen(s) found" and refuses to start gnome. i've spent days searching the net for a solution. i tried to edit xorg, disabled failsafeXserver, and did what other people suggested but still it does not work. my guess is the auto-detection of monitor(s) at boot-up should be disabled. is it possible with 8.10? are there any solution? is there a workaround for this (fake monitor)? how can i do it? help! would really like to run my box headless but with gnome running vnc for remote access. my last distro was mandrake 10.1 and i have no problems with boot-up. hopefully there is a solution. thanks!

---

### Post by sconstantin on 2009-02-07
I am having a similar issue except I am getting the "Ubuntu is running in low graphics mode" error.  I know I can just switch to Ubuntu server, but Desktop supports everything I need to do if I could just get past this issue.  Any help would be greatly appreciated.

---

### Post by JPZG on 2009-04-13
Anyone ? I'm having the same issues with a particular PC. It wont boot to the UI unless I connect a monitor to it. running ubuntu 8.10 with latest updates.

xorg conf:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Any help or points to the right directions?

---

### Post by JPZG on 2009-05-07
anyone ?

---

### Post by Dngrsone on 2009-05-07
The term is 'headless'.  Look [here](http://ubuntuforums.org/showthread.php?t=690895) and [here](http://www.ubuntuhacker.com/index.php/2007/06/04/running-ubuntu-headless-via-vnc/).

---

