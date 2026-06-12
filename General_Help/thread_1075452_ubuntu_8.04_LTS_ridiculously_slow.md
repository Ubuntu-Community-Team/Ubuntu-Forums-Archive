---
title: "ubuntu 8.04 LTS ridiculously slow"
date: 2009-02-20
forum: General Help
---

### Post by heatblazer on 2009-02-20
Here is my problem. I`ve installed ubuntu 7.10 on that hardware:

Intel Pentium 4 @1.70 GHz with 256 MB DDR Ram@400 MHz with ingegraed intel graphics. HDD ATA@ 5400 rpm.

So.. I upgraded to ubuntu 8.04 LTS. I want to say - it`s slow. Ridiculously slow. Open Office 2.4 takes forever to load. Firefox 3 is slow too. So - is it a lack of hware? How can optimize a bit? I`ve turned off all grahical extras, all navigations and views for the folders... Help... pleas :)

---

### Post by EvinK on 2009-02-20
Heatblazer, how do the applications run after they load?  Is it just the loading of the application that is slow?  I can give you a couple tips, but I don't know if they will help or not. 

Can you post the output of:

```
sudo hdparm -I /dev/sda | grep dma
```

The other thing is try a different kernel scheduler.

[LIST]
[*]Start Terminal
[*]sudo nano /boot/grub/menu.lst
[*]Find the line similar to "kernel/vmlinuz-<version> root=/dev/sdaz ro quiet splash
[*]Add elevator=cfq to the end of that line
         ex. **kernel /vmlinuz-2.6.24-23-generic root=/dev/sda4 ro quiet splash elevator=cfq**
[/LIST]

---

### Post by heatblazer on 2009-02-20
I`ll try tomorrow. Not in that PC right now. The loading time is good. But OO2.4 and FF3 are very slow. Is that normal for that hardware?

---

### Post by wildman4god on 2009-02-20
you could really stand some more ram, also try ubuntu 8.10, 8.04 was a bad release for my hardware, 8.10 worked alot better for me, but serously you need more ram, you only have the bare minimum.

edit: OO.o and firefox 3 run slow on my 1 GB of ram and 1.8 GHz cpu so thats normal, OO.o is supposed to be faster. and fire fox has alwaysed suffered proformance on linux, I don't know why.

---

### Post by heatblazer on 2009-02-20
> **wildman4god said:**
> you could really stand some more ram, also try ubuntu 8.10, 8.04 was a bad release for my hardware, 8.10 worked alot better for me, but serously you need more ram, you only have the bare minimum.

edit: OO.o and firefox 3 run slow on my 1 GB of ram and 1.8 GHz cpu so thats normal, OO.o is supposed to be faster. and fire fox has alwaysed suffered proformance on linux, I don't know why.

Thanx. That was more than enough. So it was a hw issue as I susspected. I can close the thread now :)

---

### Post by sdennie on 2009-02-20
Yes, 256M of RAM is not enough to be useful.  512M is usually ok but, 1G will almost insure that you never touch swap for normal usage.  For an older machine, the advice above about checking whether DMA is enabled on the drive is useful but, I think you'll find that no amount of tweaking will make Ubuntu run well on a 256M machine.

---

### Post by sports fan Matt on 2009-02-20
Also the OP could try Xubuntu...

---

