---
title: "Enemy Territory Brightness Issue Under Feisty"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by johnwlittle on 2007-04-23
I've noticed that the game goes quite dark during play since upgrading to Feisty. As it turns out the screensaver timer is what triggers the change. I can adjust the screensaver timer and delay the problem but I have no idea what's triggering it in the first place.

Any ideas?

---

### Post by Stalafin on 2007-04-26
I have exactly the same problem.

To change the brightness to the normal state I simply have to move the brightness-trigger a bit and then set it to it's normal state. Interestingly no game options change - it simply seems that when dragging the trigger the graphics-management returns to its normal behavior.

I don't know either what's causing this.

---

### Post by F43RY on 2007-04-27
same problem 4 me since I updated edgy to feisty. No idea why:confused: .
It's very annoying

---

### Post by hob4bit on 2007-04-29
Hi, same problem for me here. I have gone back to Ubuntu 6.10 as
its more stable. There is also the refresh rate bug with Ubuntu 7.0.4.

Now this screen saver thing gives me a clue. Why not just disable
the gnome screen saver altogether. Instead use the " xset s blank s 300"
to select the standard x-windows screen saver. If this works then I could
try and live with Ubuntu-7.0.4

I was thinking about going to Debian 4.0 instead. if this workaround
works I'll stay with Ubuntu-7.04.

It seems that Ubuntu-7.04 is a very poor quality release with regard
to graphics problems.

---

### Post by hob4bit on 2007-04-29
Hi again, rigth I trun off the Gnome screen saver and indeed the screen
brightness problem goes away in Enemy Territory.

Instead I use the standard X-Windows screen saver. Just add the
"xset s blank s 300" in the Gnome  session manager: 

   System > Preferences > Screensaver >
     Activate screensaver when session is idle > Off
  System > Preferences > Sessions >
     Startup Programs > Add > xset: xset s blank s 300 m 4,8

This selects teh "blank" screen saver after 300 seconds of idle time.
"xset" is the standard X-windows screen saver which works on all
UNIX like systems as well as Linux.

Back to Ubuntu-7.04 now.

---

### Post by aldenhg on 2007-04-29
Thanks for the fix!

---

