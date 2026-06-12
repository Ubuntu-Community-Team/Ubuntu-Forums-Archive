---
title: "desktop black screen will not respond after screen timeout"
date: 2017-01-12
forum: Desktop Environments
---

### Post by vbdanl-yahoo on 2017-01-12
hi. i have ubuntu 16.04 installed on HP amd 64bit pavilion desktop with nvidia geforce 6150 LE graphics.
i have had this problem for a long time, the screen going black after timeout setting and then sometime later not being able to get the screen or mouse to respond.
I end up having to cold boot to get the system back up.
To get around the problem, i used to just power off/on the monitor when i wasn't using it.
I think the power button is going bad on the Dell 24" monitor, so i need a better solution.
for now until i can get a real solution, i have plugged the monitor into a separate power strip that i can easily turn on/off.

i used to have the brightness/lock option set to turn screen off when inactive for 10 min.  Have it set to never for now just so i don't have to do a hard boot every day or sometimes multiple times per day.
the Power options are set to Don't Suspend, and Never show battery status in the menu bar.  (this is a desktop, not a laptop).

thanks for any help you can provide.

---

### Post by wildmanne39 on 2017-01-12
I do not know the answer to your issue but this will help you reboot it safely if the keyboard is not frozen.

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by vbdanl-yahoo on 2017-01-13
Thanks, I tried the reboot steps while the screen was working and it worked (rebooted).  Now just hoping someone has some ideas about the black screen that won't respond.

---

### Post by mörgæs on 2017-01-16
The 6100 and 6150 cards appear in the forum once in a while. Unfortunately the only solution I have found is closed-source drivers:

Do a fresh install of X/Lubuntu 16.04.1 in which you accept closed-source drivers during install (not after a reboot). Does that help?

---

### Post by vbdanl-yahoo on 2017-01-17
for now i am using the brightness controller pkg to dim the screen when not in use.  i will try your suggestion when 16.04.2 is released.
thanks for your help.

---

### Post by vbdanl-yahoo on 2017-01-24
instead of the brightness controller app i am just logging off and letting the log-in page screen saver blank the screen.  For several days now it has always came back on with cursor and allowed me to log back in.  maybe this could help others if they have lockup screen issues from the logged in screen and screen saver.

---

