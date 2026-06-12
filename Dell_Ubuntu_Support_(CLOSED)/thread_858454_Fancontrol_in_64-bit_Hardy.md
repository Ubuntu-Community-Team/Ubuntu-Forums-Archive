---
title: "Fancontrol in 64-bit Hardy?"
date: 2008-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fackamato on 2008-07-13
There's a program/kernel module called i8k, which is missing in the 64-bit version of Ubuntu. It is used for controlling the fans on Dell laptops. There's a program called i8kgui for Windows that is based on this software, and it works for me in Windows XP.

Does anyone know if it's possible to get this module to compile/somehow just get it working on a system like this?

Linux fackamato-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

---

### Post by *M* on 2008-07-14
I would also like to know the answer to this, but for all computers, I modded my powersupply fans to stop the thermal override making them loud and just hooked them up to one of the system fan pins of the mobo, I can control it with speedfan in windows but in ubuntu they always go at 100%.

---

### Post by bubbalouie on 2008-07-18
I personally don't use a fan control application anymore, however, this should work just fine:

[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)

you might need to install build-essential from the repos (just to ensure a compiler and libc etc, however, I am fairly confident everything you need to compile this is included by default). if not:

sudo apt-get install make build-essential

Be warned though, if things get hot they will break, trying to reduce power usage to minimise heat may be a good idea (especially if you intend on forcing lower fan speeds). I hope this helps.

Cheers

Ryan

---

