---
title: "Raid Format"
date: 2009-05-22
forum: General Help
---

### Post by unclejac on 2009-05-22
So question straight away here: Should you format before you set up a RAID or after you set it up?

I'm thinking format after you have set the RAID up ? 

So here is the background.

I got a couple of disks I'm trying to set up as RAID 1 on my Ubuntu 9.04 AMD64 box. (not a RAID for the boot / filesystem)

So the drives are setup in the BIOS correctly as RAID 1. 

dmraid seems to think the RAID is active

```
betai@BETA:~$ sudo dmraid -r
[sudo] password for betai: 
/dev/sdb: nvidia, "nvidia_fjjgdajc", mirror, ok, 976773166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_fjjgdajc", mirror, ok, 976773166 sectors, data@ 0

``` 

However I know its not formatted yet. Looking at gparted the filesystem is unallocated.

So if you proceed to format /dev/mapper/nvidia_fjjgdajc with the filesystem ext3 you get a partition called /dev/mapper/nvidia_fjjgdajc1. This seems to be called Model: Linux device-mapper (mirror)

Another drive appears on the list called /dev/mapper/nvidia_fjjgdajc1 with the partiton name /dev/mapper/nvidia_fjjgdajc11. This seems to be called Linux device-mapper (linear) But I notice there is an exclamation error mark next to this one.

So I'll go try and mount this now. Put a line in my FSTAB along the lines:

```
/dev/mapper/nvidia_fjjgdajc1 /media/RAID1 ext3 defaults 0 2 
```
(I'm guessing here) 

ok off to try it. 

p.s. Do you ever feel like you are talking to yourself ? :D

---

### Post by unclejac on 2009-05-22
So it would seem that works :D problem solved

---

### Post by misterfixit on 2009-05-22
> **unclejac said:**
> So question straight away here: Should you format before you set up a RAID or after you set it up?

I'm thinking format after you have set the RAID up ? 

So here is the background.

I got a couple of disks I'm trying to set up as RAID 1 on my Ubuntu 9.04 AMD64 box. (not a RAID for the boot / filesystem)

So the drives are setup in the BIOS correctly as RAID 1. 

dmraid seems to think the RAID is active

```
betai@BETA:~$ sudo dmraid -r
[sudo] password for betai: 
/dev/sdb: nvidia, "nvidia_fjjgdajc", mirror, ok, 976773166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_fjjgdajc", mirror, ok, 976773166 sectors, data@ 0

``` 

However I know its not formatted yet. Looking at gparted the filesystem is unallocated.

So if you proceed to format /dev/mapper/nvidia_fjjgdajc with the filesystem ext3 you get a partition called /dev/mapper/nvidia_fjjgdajc1. This seems to be called Model: Linux device-mapper (mirror)

Another drive appears on the list called /dev/mapper/nvidia_fjjgdajc1 with the partiton name /dev/mapper/nvidia_fjjgdajc11. This seems to be called Linux device-mapper (linear) But I notice there is an exclamation error mark next to this one.

So I'll go try and mount this now. Put a line in my FSTAB along the lines:

```
/dev/mapper/nvidia_fjjgdajc1 /media/RAID1 ext3 defaults 0 2 
```
(I'm guessing here) 

ok off to try it. 

p.s. Do you ever feel like you are talking to yourself ? :D
  Yes, lots.  I think a lot of the helpers who used to be here are out tinkering with some other brand new stuff; after all, Ubuntu isn't cutting edge anymore .. it's just sort of "oh, yeah, it works".  I've been using Linux since 1998 a,d find something every day which is either puzzling or intriguing.  I've gotten most of my education on Linux from forums on usenet -- which used to be great until the net nazi's and other arshlocken took them over.

---

### Post by misterfixit on 2009-05-22
> **misterfixit said:**
> Yes, lots.  I think a lot of the helpers who used to be here are out tinkering with some other brand new stuff; after all, Ubuntu isn't cutting edge anymore .. it's just sort of "oh, yeah, it works".  I've been using Linux since 1998 a,d find something every day which is either puzzling or intriguing.  I've gotten most of my education on Linux from forums on usenet -- which used to be great until the net nazi's and other arshlocken took them over.



See here is my dmraid -l

dave@dave-desktop:~$ sudo dmraid -r
[sudo] password for dave: 
/dev/sdd: nvidia, "nvidia_jfgfbeha", mirror, ok, 1465149166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_jfgfbeha", mirror, ok, 1465149166 sectors, data@ 0
dave@dave-desktop:~$ 

Same as you.

Still thrashing away...

---

