---
title: "Keyboard slow responce"
date: 2006-10-20
forum: Desktop Environments
---

### Post by robinl on 2006-10-20
My keyboard just suddenly became very unresponsive: it takes like a second holding down the key in order for it to appear on screen. This happens everywhere on my main account and the computer beeps whenever I press a key (well not really beep since I disabled it, but beryl give the window a bounce which means the same thing anyways). I'm now in the other GNOME session (the failsafe one? Can't remember the name) and everything works fine so I suspect it is in my settings. How can I get a default setting on that only while preserving my other settings in GNOME? Thanks.

---

### Post by barisurum on 2007-04-17
There is an option in KDE that when you press a key more than 8 seconds it asks you to activate the Slow Keys mode. Maybe you activated it.

   To solve this go to  System Settings -- Regional and Accesibility -- Accesibility -- There is a tab named Keyboad Filters, disable Use Slow Keys

---

### Post by jagamans on 2007-10-09
I am using WINXP on a Dell Inspirion Notebook and had the same proplem with slow keyboard responce.  I was able to resolve the proplem by disabling PCMservice.exe.  You can do this by going into msconfig and clicking on startup.

If you don't have PCMservice try disabling all startup modules rebooting and see if the problem goes away.  If it does then you will need to nit pick your way through the modules in startup until you find the culprit.

Good luck,

John:lolflag:

---

### Post by kryptontri on 2007-10-17
Is anyone else seeing this? My keyboard has slowed down without any reason since last week, i have looked for any infor and it seems this is not the only report as there are people askijng the same question..

Any ideas what i can do short of reinstalling ubuntu ?? ;-9

Btw this is fiesty:
Linux matrix 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux

:confused:

---

### Post by robinl on 2007-10-21
Does it go away if you make a new account? Make sure Slow keys in System/Preferences/Keyboard/Accessibility/Slow keys is disabled.

---

