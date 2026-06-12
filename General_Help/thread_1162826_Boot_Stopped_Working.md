---
title: "Boot Stopped Working"
date: 2009-05-18
forum: General Help
---

### Post by s.fox on 2009-05-18
Hi,

A machine I use at work has a WUBI installation that has gone wrong.  It is no longer booting like normal and instead boots into GRUB4DOS 0.4.4  .    I am unsure as to what has been changed on the system,  but I gather a coleague of mine pulled the plug on the machine.  Since then it no longer boots.

Pressing escape in GRUB4DOS gives me several different options.  They are:

```
find /ubuntu/disks/boot/grub/menu/lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
```

The first one gives a file not found error,  and the others just go into GRUB4DOS.   I am a bit stuck and not sure how or what to do to fix this.   Can someone please assist?

Thank you for any help,  much appreciated.

-Ash R

---

### Post by s.fox on 2009-05-19
1 day bump :)

---

### Post by VMC on 2009-05-19
> **Ash R said:**
> ...but I gather a coleague of mine pulled the plug on the machine.  Since then it no longer boots.

Pressing escape in GRUB4DOS gives me several different options.  They are:

```
find /ubuntu/disks/boot/grub/menu/lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
```


It appears that Ubuntu directory was removed. Can you verify that? That's the first step. I've never used wubi so I'm unsure as to how the boot works. I was under the impression that Windows boot was used. I see that it uses grub4dos.

---

### Post by s.fox on 2009-05-19
Hi,

Thanks for the advice.  I'll check that out when I am next at work.

I also saw [this]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu"),  which may be worth investigating.  

I'll report back after the tests.

-Ash R

---

### Post by s.fox on 2009-05-22
Hi,

I was able to fix it from within Windows.    I ran this in command prompt:

```
chkdsk /r
```

Thanks you for the help.

-Ash R

---

