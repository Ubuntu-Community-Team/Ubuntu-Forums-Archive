---
title: "What's i386?"
date: 2009-01-07
forum: Gaming &amp; Leisure
---

### Post by grnida on 2009-01-07
We're fairly new to Ubuntu and Linux.  I'm trying to add new games under 'applications-add&remove programs' however I get a message that states: "(Game name) cannot be installed on your computer type (i386).  Either application requires special hardware features or the vendor decided to not support your computer type.

How can I get correct features or find games suitable for my computer type?  Thanks!

---

### Post by Sockerdrickan on 2009-01-07
x86 32bit

the app you want to install is probably compiled for x86 64bit or powerpc

---

### Post by Shpongle on 2009-01-07
its the 32 bit form of the 80x86 architecture, i had problems like that initially when i first started using ubuntu, have you got the all the system updates ??, that seemed to fix it for me

---

### Post by eragon100 on 2009-01-08
> **DillByrne said:**
> its the 32 bit form of the 80x86 architecture, i had problems like that initially when i first started using ubuntu, have you got the all the system updates ??, that seemed to fix it for me

There are a few, *very* few, that can only be compiled for either 32 or 64 bit (usually only for 32 Bit, actually). Packages are automatically build by the launchpad compile systems. If they fail to compile for a certain architecture, then the corresponding package will not be available.

---

