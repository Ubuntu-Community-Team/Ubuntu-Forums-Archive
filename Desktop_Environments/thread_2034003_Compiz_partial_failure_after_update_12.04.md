---
title: "Compiz partial failure after update 12.04"
date: 2012-07-27
forum: Desktop Environments
---

### Post by pdr2esmolbra on 2012-07-27
Hello everyone, 

I have a 32bit PC with 12.04 Ubuntu. It has a Radeon ATI graphics (Cedar Pro, Radeon HP 5450) card and I installed catalyst to get better performance.

After an update yesterday, my desktop has been really slow. The Alt-tab application switcher that used to be very nice was reduced to a windows-xp like switcher with very small tabs.  Also the start button runs very slow.

I tried:

unity -- reset

but got many Fatal errors with compiz in general.

This command didn't work either:  gconftool-2 --recursive-unset /apps/compiz-1

I got the compiz manager, but any changes I made are not applied, even after restart...

I am a little hesitant to reinstall the whole compiz and/or in case the desktop fails completely? Is it safe to do that considering I have the radeon 3rd party graphics drivers? 

Any advice is highly appreciated!

Thanks!
Pedro

---

### Post by zombifier25 on 2012-07-27
The XP-like switcher suggests that you're not using Ubuntu 3D. Run this and post the output:
```
echo $DESKTOP_SESSION
```
if the output is 'ubuntu', then it's Ubuntu 3D. If it's 'ubuntu 2d', then it's Ubuntu 2D.

---

### Post by pdr2esmolbra on 2012-07-31
Thanks zombifier25,

Turns out I have ubuntu2D.
However, I solved the problem by reinstalling the catalyst drivers, everything runs smoothly and the Alt Tab and Super+W are back!

I sometimes have the compiz crashing randomly tough. It is a pitty that ubuntu updates conflict with non-ubuntu graphics drivers.

Thanks for your help!
Pedro

---

