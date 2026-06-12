---
title: "Running .exe without WINE (FlashJester Jugglor Engine)"
date: 2006-02-15
forum: Desktop Environments
---

### Post by Mac_Switcher on 2006-02-15
Please close this thread.

---

### Post by dcstar on 2006-02-16
[QUOTE=Mac_Switcher]I'm doing Information Systems through distance ed and I need to run an exe file on mu Ubuntu iBook (also running OS X Tiger) right-clicking on the .exe file (under \/\/|nd0zeXP) shows a description of "FlashJester Jugglor Engine". This looks to be some kind of Shockwave Flash program (which it is, I think).

Is there a way to convert this so its a normal ShockWave Flash file that will run on Ubuntu? Or should I use WINE?

Thanks for any help.[/QUOTE]
An .exe is a Windows file for a Windows environment, what is inside it needs to be run in such, or in wine on Linux.

---

### Post by slux on 2006-02-16
You won't be able to use wine to run it on an ibook because it depends on the computer having the same processor architecture as the executable (this will no longer be a problem on the new intel macs of course).

your options are to use full-blown emulation (qemu, bochs, etc.) which will probably work slowly if you have any sort of complex animation to display and especially if it's flash which is dog-slow to begin with. Another would be to get the flash out of the executable somehow but I have no idea if that's feasible and after that you'd need to have some sort of a flash player which aren't exactly state of the art or robust on Linux PPC presently. Gnash or even gplflash2 may eventually get there I guess.

---

### Post by Mac_Switcher on 2006-02-16
Please close this thread.

---

### Post by slux on 2006-02-17
Qemu and bochs also require you to install the operating system on a virtual disk drive and I'm a bit pessimistic on them offering acceptable speeds for your particular application. It looks like they're not included on the install cd so you'd also have to download the packages separately. BTW, what exactly is FlashJester Jugglor Engine? :P

---

