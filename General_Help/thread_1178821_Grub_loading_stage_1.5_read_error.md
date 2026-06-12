---
title: "Grub loading stage 1.5 read error"
date: 2009-06-04
forum: General Help
---

### Post by ubna on 2009-06-04
[SIZE=4][COLOR=Magenta][I]Hi, I've got a windows 32 bit processor with Windows XP Professional installed on it and was installing UBUNTU on my external hard drive (500GB) So it finished installing it, restarted and got 2 errors. 
[/I] 
**1. This is error 1, I have an error saying grub loading error 21, **[I]this is without my external hard drive plugged in.
[/I]
**2. Grub loading stage 1.5 read error,** [/COLOR][/SIZE][COLOR=Magenta][I][SIZE=4]this error is when I plug in my external hard drive and turn it on.

[/SIZE][/I][/COLOR][SIZE=4][COLOR=Magenta][I][B]This is my boot order
1:  1st floppy drive
2:  HDD: PM_ST3320620AS
3: CDROM:4M_TSSTTCORP_CDDVDW_SH-S20
4: IDE:ATAPI_CDRW_52X32[/B][/I][/COLOR][/SIZE]
[COLOR=Magenta][/COLOR] [COLOR=Magenta][I][SIZE=4] 
Greatly appreciated if you could help.

- :KS Ubna :KS[/SIZE]
[/I][/COLOR]

---

### Post by VMC on 2009-06-04
With the Ubuntu drive plugged in, boot from a livecd and from a terminal(Applications>Accessories>Terminal) type the following commands:

```
sudo fdisk -l
```

---

### Post by ubna on 2009-06-07
> **VMC said:**
> With the Ubuntu drive plugged in, boot from a livecd and from a terminal(Applications>Accessories>Terminal) type the following commands:

```
sudo fdisk -l
```

Do I post the results?

---

