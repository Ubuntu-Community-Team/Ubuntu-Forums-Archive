---
title: "Ubuntu lags/freezes when user is idle"
date: 2010-01-27
forum: Desktop Environments
---

### Post by JoyousDeath on 2010-01-27
After about 30 minutes to 2 hours Ubuntu will stop completely until the mouse moves again, I had a theory about it being a dynamic ticks problem but was unsure how to edit the new version of grub (Beta).

System specs:

Ubuntu 9.10 Karmic
Kernal Linux 2.6.31-17-generic
Gnome 2.28.1

Intel Celeron Processor 420

1024MB Memory

120 GB hard drive

Intel graphics media accelerator 950

---

In an unrelated problem though may be the source my hard drive reports to have many bad sectors (odd since Windows Vista didn't detect anything). Specifically the report says "Current Pending Sector Count. Number of sectors waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector, it will only be remapped on a failed write attempt."

But after looking I thought that was just a comparability issue with my hard drive (not sure about this).

Hard drive is a Seagate Barracuda 7200.10 HP Pro #GN571AA#ABA.
S/N: 5RX1VJXB

---

### Post by JoyousDeath on 2010-01-27
Oh, also, the self check came back OK.

---

### Post by JoyousDeath on 2010-01-27
bump

---

### Post by woodmaster on 2010-01-27
I had similar lagging freezing I fixed by reverting to older graphics drivers by following this here:
```
Originally Posted by pompiuses 					[[IMG]http://ubuntu-ky.ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8576889#post8576889") 				
 				[I]Looks like there's a cure afterall :smile:. Disabling Compiz and installing the Xorg intel driver to 2.4 fixed it completely. So at least on my Dell Dimension 2400 the problem was graphics related.

Following this post:
[http://ubuntuforums.org/showpost.php...0&postcount=15]("http://ubuntuforums.org/showpost.php?p=8341830&postcount=15")[/I]

```

---

### Post by JoyousDeath on 2010-01-27
Thank you, I'll go try this now.

I'll post back tomorrow to say solved/unsolved.

---

### Post by JoyousDeath on 2010-01-30
Sorry about the long absence, but two days of non-stop running and no problem.

Thank you, woodmaster.

---

