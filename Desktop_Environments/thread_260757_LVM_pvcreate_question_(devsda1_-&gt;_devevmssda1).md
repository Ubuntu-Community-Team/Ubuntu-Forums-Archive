---
title: "LVM pvcreate question (/dev/sda1 -&gt; /dev/evms/sda1)"
date: 2006-09-19
forum: Desktop Environments
---

### Post by bhartsock on 2006-09-19
I just started playing around with LVM for the first time a couple days ago.  I ran into a couple issues.  (Forgive me for not having the exact output, I am writing this from memory away from my desktop)

Issue 1 (minor):
My new IDE HD was recognized as /dev/sda which I thought sd* was reserved for only Sata/Scsi (but everything works so I don't care too bad)

Issue 2:
```
pvcreate /dev/sda
```
I get some warnings, but it does successfully create the physical volume.

```
vgcreate vg /dev/sda
```
Fails, says device /dev/sda unreadable

Here is the interesting part
```
pvdisplay
```
Lists physical device as /dev/evms/sda

Why is pvcreate seeing the device with the evms directory, while fdisk still reads it as /dev/sda1?

(BTW, ```
vgcreate vg /dev/evms/sda
``` seems to work so I am not too worried, but it still somewhat disheartening not knowing what is going on)

Thanks for your help.

---

