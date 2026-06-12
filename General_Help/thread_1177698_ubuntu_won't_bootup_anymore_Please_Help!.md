---
title: "ubuntu won't bootup anymore Please Help!"
date: 2009-06-03
forum: General Help
---

### Post by stick2it on 2009-06-03
I followed this link to setup pilot for my pda.  
[http://ubuntuforums.org/showthread.php?t=523434](http://ubuntuforums.org/showthread.php?t=523434)
I installed linux-kernel headers today and rebooted now my ubuntu is stuck on bootup.  
It says 
*setting kernel variables
findfs: unable to resolve 'UUID=8f275f7f-739f-4dc3-b4eb-a862367a75df'
*activating swap . . . 
and its been stuck here for hours.  
What do I do now?  I have files on this comp which I REALLY need.  I can't reinstall Ubuntu without getting these files off first.

Please help

---

### Post by stick2it on 2009-06-03
If I just know how to get to my desktop so that I can remove linux kernel header then I can resolve this issue?

If not then maybe someone can tell me how to restore ubuntu without losing my data??

---

### Post by michy99 on 2009-06-03
On booting, do you have the option of booting to an earlier kernal?

---

### Post by stick2it on 2009-06-03
I used Esc to get me to the menu option which allows me to choose ubuntu with Kernel (recovery mode)  
I tried that and it didn't work

---

### Post by MRSAMASTER on 2009-06-03
An option would be to put in a Live CD and boot that to get your files off.

---

### Post by stick2it on 2009-06-03
perfect Thank you.

---

### Post by VMC on 2009-06-03
From the recovery mode, type the following, or better still, use that livecd and capture the output of the following commands:

```
ls /boot/vm*
sudo blkid
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

