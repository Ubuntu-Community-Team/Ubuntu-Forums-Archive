---
title: "networking autodetects my modem while gnome ppp doesn't"
date: 2005-10-07
forum: Desktop Environments
---

### Post by NemanjaM on 2005-10-07
I had just installed dial-up hsf conexant modem and my networking panel recognizes it(autodetect) and when I get to gnome ppp and do the same thing it does not(''No modem was found on your system''), and when I try to connect using it it says:

--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied

Please tell me how to solve this problem!

Thank you for your time

---

### Post by NemanjaM on 2005-10-07
Maybe i oght to try another approach.

A friend of mine has this really old modem which he is willing to give to me. Actually it seems like it is not a modem(as google says) but a AMR(Audio/Modem Riser). Since he does not have it on his own he was able to find User Guide and gave it to me to study it through.

These are the features:
ITU 56K V.90 standard
AC'97 2.1 Compliant
Windows 95/98, NT5(I was really glad when I red this. Since it does not support xp(at least didn't when it showed up) it must have been on the market for some time, and might not be a soft. modem)
Software upgradeable

Tell me what you think about that, please.

Thank you for your time

---

### Post by Envel on 2005-10-08
[QUOTE=NemanjaM]I had just installed dial-up hsf conexant modem and my networking panel recognizes it(autodetect) and when I get to gnome ppp and do the same thing it does not(''No modem was found on your system''), and when I try to connect using it it says:

--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied

Please tell me how to solve this problem!

Thank you for your time[/QUOTE]

Start gnome-ppp with gksudo (gksudo gnome-ppp), or change access mode every time after boot on /dev/modem.

---

