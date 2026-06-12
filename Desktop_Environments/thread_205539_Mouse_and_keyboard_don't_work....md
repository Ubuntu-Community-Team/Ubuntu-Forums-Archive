---
title: "Mouse and keyboard don't work..."
date: 2006-06-28
forum: Desktop Environments
---

### Post by jespdj on 2006-06-28
I have just downloaded Ubuntu Linux 6.06 and burned it on a CD.

Unfortunately, when I boot my desktop computer with this, the mouse and keyboard don't work at all.

The keyboard does work in the boot menu - I can select one of the options. But after booting, when I see the desktop, both mouse and keyboard don't work at all. The only thing I can do is switch the system off using the power button. Ctrl-Alt-Del doesn't work either.

I have a cheap brand (Nortek) wireless USB keyboard and mouse. I have enabled USB keyboard and mouse support in the BIOS. I can see that the devices do work - the light on the receiver blinks, which means it receives the wireless signal of the mouse and keyboard.

I tried a PS/2 mouse instead, but that doesn't work either.

I tried it on my laptop, and there it works without any problems.

Why doesn't it work on my desktop computer? ](*,)

---

### Post by jespdj on 2006-06-28
Fortunately I found the solution myself! I have to boot with an extra kernel parameter:

**acpi=off**

With this extra parameter my mouse and keyboard work without any problem.

---

