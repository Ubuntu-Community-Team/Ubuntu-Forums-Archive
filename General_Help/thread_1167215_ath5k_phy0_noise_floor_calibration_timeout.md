---
title: "ath5k phy0: noise floor calibration timeout"
date: 2009-05-22
forum: General Help
---

### Post by TripleG on 2009-05-22
Hey everyone, thanks for the wonderful effort in helping newbies like me.
I have recently upgraded to Jaunty Jackalope, and have immediately noticed a recurrent line coming up randomly in the terminal: "ath5k phy0: noise floor calibration timeout".
It was harmless at the beginning, and the os kept working well until a few days ago, when it started freezing and getting my graphical interface out of use. what i get to see is the screen becoming gradually black and the only way out is to reboot it or turn it off from Ctrl+Alt+F1,2,3,4,5 or 6. When restarted, it will do the same, even with the wireless manually turned off.
As said, I've just started learning something about Linux, i'm enjoying it a lot, but until now i have always found the solutions to my problems on the forum. Not this time.......
Anyone that can help me?

---

### Post by dc740 on 2009-09-22
sure, just download this drivers:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

Why stable? cause I tried the bleeding edge release today and it gave me a lot of headaches, first to make it compile, and after that it refused to work.

Currently I'm using:
compat-wireless-2.6.31-rc7.tar.bz2

and the problem has disappeared. Also you will noteice that your signal strength is way higher and stable :)

About the display. it seems that it's a completely different issue. It has nothing to do with your wireless card

Good luck! :)

---

### Post by solomonson on 2010-12-24
Installing that package actually made the problem worse for me.

---

