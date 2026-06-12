---
title: "Could not activate swap"
date: 2009-01-21
forum: General Help
---

### Post by matt_wood87 on 2009-01-21
Hi people,

i'm having a bit of trouble with my ubuntu install 8.10.

I have ubuntu running as part of a dual boot setup up with windows on my laptop. when i initially set up ubuntu i only created a small partition to install it on, as i have been aproaching using all the available space i shrunk my windows partition to create some space to extend my linux partion in to.

having shrunk windows i loaded up ubuntu, started the partition editor and looked at my partitions:

|  Windows  | free space | linux-swap | ubuntu |

to extend my ubuntu partition i figured i needed to move my linux swap along the drive so the free space was next to my Ubuntu partition. i right clicked the linux swap partition and selected swapoff, moved it along the free space so it now looks like:

|  Windows  | linux-swap | free space | ubuntu|

however now i am unable to turn the swap on, when i right click and select swapon i get the error "could not activate swap" "swapon: /dev/sda2: invalid argument"

so my two questions are.

1. how do i get swapon

2. how do i extend my linux partition into the freespace next to it


many thanks for taking the time to read my post.

Matt Wood

---

### Post by Tim Sharitt on 2009-01-21
Open a terminal and do
```
sudo fdisk -l
```
Then using the partition listed as swap
```
sudo swapon /dev/sdax
```
replacing x with the number of the partition.

To automatically turn on swap at startup, add line to your /etc/fstab
```
/dev/sdax        none            swap    sw              0       0
```

You can expand your partition with with gparted on the LiveCD. You may have to move the partition into the free space first, as you can only expand from the end of the partition.

---

### Post by matt_wood87 on 2009-01-21
Hi,

thanks for the quick reply!

i tried what you suggested and here's the terminal output:

matthew@mtw:~$ sudo fdisk -l
[sudo] password for matthew: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bf4489f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         639       13313   101804024    7  HPFS/NTFS
/dev/sda2           13314       13554     1935832+  82  Linux swap / Solaris
/dev/sda3           13555       17151    28892160    7  HPFS/NTFS
/dev/sda4           17152       19457    18522945   83  Linux
matthew@mtw:~$ sudo swapon /dev/sda2 
swapon: /dev/sda2: Invalid argument

any suggestions as to why it didnt work?

thanks

Matt

---

### Post by Tim Sharitt on 2009-01-21
There may be something wrong with the swap partition (corrupted fs or something)

Try to reformat the swap partition
```
sudo mkswap /dev/sda2
sudo swapon /dev/sda2
```

---

### Post by matt_wood87 on 2009-01-21
that worked perfectly.

thanks for your help!

Matt

---

### Post by caljohnsmith on 2009-01-21
If you don't do anything further, I just thought I would mention that you will need to run that swapon command every time you login in order to use swap. If you want to have swap automatically mounted on start up, I would suggest doing:
```

sudo swapoff -a && sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda2
```
What that does is change the UUID of your swap partition back to what it was originally, so assuming you previously were able to use your swap OK (it should be in your /etc/fstab), then that should make it so your swap will be automatically mounted on start up. Doing it that way I think is easier, because otherwise you have to edit your /etc/fstab file and /etc/initramfs-tools/conf.d/resume file with the new swap UUID, and also regenerate all your initrd images in /boot since they are hard-coded with the original swap partition UUID. But if you are happy with running swapon every time you boot into Ubuntu, that's perfectly OK too.

---

### Post by matt_wood87 on 2009-01-24
is it not possible to add the line

sudo swapon /dev/sda2

to a file that is run on startup so it runs without me typing it, and i can keep this setup?

---

