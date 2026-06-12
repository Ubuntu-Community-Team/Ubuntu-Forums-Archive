---
title: "Login Error (hopefully)"
date: 2009-03-25
forum: General Help
---

### Post by bill_riley on 2009-03-25
Good day all!
So I'm having a problem with a PC I'm putting Ubuntu on: When the user logs on, it responds like it is loading onto the desktop screen, but it freezes half way, before the wallpaper is loaded (or anything for that matter). The cursor still appears, and it responds, but everything else is null.

I'm not entirely sure how to fix this, so if anyone else has had this problem, I would greatly appreciate the help.

PS: I'm installing v8.10, on an insignia d400a, if it would come in handy.

---

### Post by jb77450 on 2009-07-26
I've been putting kubuntu 0810 on an old d400a this weekend and saw the exact same thing.  I get the hard disk icon after logging in and other icons start to appear, but while they are fuzzy the loading stops but the machine is still responsive.  I was able to find two workarounds for this:
1. Reboot to the login prompt and use CTRL-ALT-F1 to bypass x-windows / kde.  Login, do an "aptitude update", "aptitude dist-upgrade", and "reboot" and then I was able to login fine.
2.  Do a safe-mode install (use F4 at the install screen).

I think it is the buggy drivers for the embedded intel 845 video that is causing the problems..

I am VERY interested to know if you have ubuntu running smoothly on your d400a.  I get  lockups anywhere from a few minutes to 6-8 hours after a reboot.  I have not been able to track down the problem, but am still looking into it but have not been able to get anywhere.

---

