---
title: "Can't run ePSXe"
date: 2010-06-03
forum: Emulators
---

### Post by PyngThyng on 2010-06-03
I previously had ePSXe installed on Karmic and it ran fine. On Lucid I get as far as the opening menu screen but if I try to run anything or configure the plug-ins it shuts down. When run in the console I get this message: 

* Running ePSXe emulator version 1.6.0. 
plugins/libgpuPeopsMesaGL.so.1.0.78: undefined symbol: glColorTableEXT

Can anyone help? Thanks. :confused: ](*,)

---

### Post by disturbedite on 2010-06-03
maybe try this: [http://ubuntuforums.org/showthread.php?p=9405021#post9405021](http://ubuntuforums.org/showthread.php?p=9405021#post9405021)

---

### Post by aseptilena on 2012-03-14
[SOLVED:KS]
Wow, obviously it's just simple. To solve this bug we should remove the error library. If U installed epsxe from ppa, you can type these on terminal :

sudo rm /usr/share/games/epsxe/plugins/libgpuPeopsMesaGL.so.1.0.78

and

sudo rm .epsxe/plugins/libgpuPeopsMesaGL.so.1.0.78

-------------------
Those commands will remove the error library from ur home and system

If u just download it and extract, just remove the error library.

If u have another error library, just remove it or replace it with the fixed one. Just googling please...
Thanks for Ur attention, and have a nice day with Ubuntu...
Hopefully helpful... :D

---

