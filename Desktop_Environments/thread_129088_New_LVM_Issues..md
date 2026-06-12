---
title: "New LVM Issues."
date: 2006-02-12
forum: Desktop Environments
---

### Post by chomafin on 2006-02-12
Hello,
I am currently attempting to set up a New LVM on an existing Ubuntu Breezy setup.  I seem to be having a bit of trouble. 

My current setup consists of 3 hdd's.  I would like to make hdb and hdc into one LVM.  I have got everything semi setup, where im having troubles is getting all the space allocated.

I have created, and recreated, the LV a few times now trying different things.  It will not let me increase past te size of the first disk.  My first attempt I created the LV using 38G; and when trying to extend the group it would only allow it the extra .12G.  So I removed the group, and tried recreating it w/ the 75G that a pvscan shows, But it would say the same error.

When trying to extend my VG to its full size, I get the error.

```
# lvextend -l +1190 /dev/MainVG/lv_ftp
  Extending logical volume lv_ftp to 75.31 GB
  Insufficient allocatable extents (1220) for logical volume lv_ftp: 2410 required

``` 

```
# pvscan
  PV /dev/hdc1   VG MainVG   lvm2 [38.12 GB / 38.12 GB free]
  PV /dev/hdb1   VG MainVG   lvm2 [37.19 GB / 37.19 GB free]
  Total: 2 [75.31 GB] / in use: 2 [75.31 GB] / in no VG: 0 [0   ]

``` 
```
# pvdisplay
  --- Physical volume ---
  PV Name               /dev/hdc1
  VG Name               MainVG
  PV Size               38.12 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       32768
  Total PE              1220
  Free PE               0
  Allocated PE          1220
  PV UUID               8Yw0AH-gpoC-mgSN-ABIs-b5Es-7t3I-Kx4usH

  --- Physical volume ---
  PV Name               /dev/hdb1
  VG Name               MainVG
  PV Size               37.19 GB / not usable 0
  Allocatable           yes
  PE Size (KByte)       32768
  Total PE              1190
  Free PE               1190
  Allocated PE          0
  PV UUID               m7v0PT-39RJ-fN5L-7Hl2-WeoA-mCzU-qwj6CP

``` 


```
# vgdisplay
  --- Volume group ---
  VG Name               MainVG
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               75.31 GB
  PE Size               32.00 MB
  Total PE              2410
  Alloc PE / Size       1220 / 38.12 GB
  Free  PE / Size       1190 / 37.19 GB
  VG UUID               gOdDZG-epmK-8DSW-doAD-h6op-VWo8-bkfCPz



``` 
I have attempted googleing about, with no success so far.

Links used : 
[LVM How-To]("http://www.tldp.org/HOWTO/LVM-HOWTO/index.html")
[LVM How-To]("http://www-128.ibm.com/developerworks/linux/library/l-lvm/")

---

### Post by chomafin on 2006-02-13
Bump for the day time folks..  No new progress :(

---

### Post by vrecan on 2006-02-13
This happens if you create the Logical Volume using the -C option.  If you use lvchange lvmpath -C n and then try and extend your LVM it should work fine.

---

### Post by chomafin on 2006-02-15
If anyone is interested, Running :
 ```
lvchange <LVM Path> -C n
```

Did allow me to use all of the avilable PE's.

---

