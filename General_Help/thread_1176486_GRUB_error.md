---
title: "GRUB error"
date: 2009-06-02
forum: General Help
---

### Post by lilnate22 on 2009-06-02
ok well this has happened 2x so far (on 2 different computers) and for the life of me, i cant figure out why its happening.

i have 2 HDs (two seperate, 1 internal, 1 external e-SATA)

the first HDD (we will call this HDDA) contains windows
the second HDD (call this HDDB) just got a fresh installation of ubuntu 9 

HDDB is on the external, while HDDA is internal. when i try to boot HDDA **without** 
HDDB being connected, i get:
"GRUB HD ERROR"

now for the life of me, im not understanding WHY this would be the case... i didnt even TOUCH the HDDA during installation, but for the life of it, it will not boot up.


luckily i have ANOTHER HDD that contains another copy of windows, when i replace that with the HDDB, i can boot up windows (though not the same as HDDA) looking inside HDDA i can still see all my files from windows is still there...including all my programs/drivers etc etc..


any suggestion how to get the GRUB error fixed?

---

### Post by VMC on 2009-06-02
> **lilnate22 said:**
> ok well this has happened 2x so far (on 2 different computers) and for the life of me, i cant figure out why its happening.

i have 2 HDs (two seperate, 1 internal, 1 external e-SATA)

the first HDD (we will call this HDDA) contains windows
the second HDD (call this HDDB) just got a fresh installation of ubuntu 9 

HDDB is on the external, while HDDA is internal. when i try to boot HDDA **without** 
HDDB being connected, i get:
"GRUB HD ERROR"

now for the life of me, im not understanding WHY this would be the case... i didnt even TOUCH the HDDA during installation, but for the life of it, it will not boot up.


luckily i have ANOTHER HDD that contains another copy of windows, when i replace that with the HDDB, i can boot up windows (though not the same as HDDA) looking inside HDDA i can still see all my files from windows is still there...including all my programs/drivers etc etc..


any suggestion how to get the GRUB error fixed?

Try booting up a livecd and type:

```
sudo fdisk -l
```

also

```
sudo blkid
```

---

### Post by djuliette on 2009-06-02
I'm not sure if this is right, but perhaps check the /boot/grub/menu.lst file for entries to that hard drive and comment them out.

---

### Post by lilnate22 on 2009-06-02
> **VMC said:**
> Try booting up a livecd and type:

```
sudo fdisk -l
```also

```
sudo blkid
```
now im not really 100% familiar with GRUB, but if i run that off on a live CD, how will i tell it to "fix" HDDA (aka the windows HD)

---

### Post by VMC on 2009-06-02
> **lilnate22 said:**
> now im not really 100% familiar with GRUB, but if i run that off on a live CD, how will i tell it to "fix" HDDA (aka the windows HD)

Has nothing to do with Grub. It tells us how your drives are mapped out.

---

