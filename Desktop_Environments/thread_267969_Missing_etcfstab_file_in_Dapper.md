---
title: "Missing /etc/fstab file in Dapper"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Dynapen on 2006-09-29
Using 6.06 (Dapper) on my laptop. Worked the other day to get my NFTS partition to be mounted. As the first step I made a backup of the /etc/fstab file. But before I was able to get any farther on the mounting issue, I had to jump to another problem. 

2 days later (this is my home machine that is broken) I try to boot the machine into Ubuntu to finsh the NTFS mount stuff, but the machine won't finishing initializing, and is reporting errors of missing /etc/fstab. This makes me believe that I performed a 
     mv /etc/fstab /etc/fstab.bak instead of a 
     cp /etc/fstab /etc/fstab.bak

The good news is that I have a good version of the fstab file that I can use, the bad part is that I can't get into the system to rename the file. 

How can I get into some sort of rescue mode where I can have root access to cp my .bak file back into the original location of /etc/fstab?

I have tried using the install CD and running as a live mode, but it doesn't successfully mount all the partitions, including the / partition, so I can't get at the file that way. Tried using Knoppix to do the same, still no luck. 

Anyone got advice on what to try?

---

### Post by wieman01 on 2006-09-29
You need to run the Live CD and mount your root partition. Once you have loaded the Live CD, open a terminal and do this (assuming that **hda1** is your root partition... simply change it if necessary): 
> sudo mount /dev/hda1 /mnt
> sudo cp /mnt/etc/fstab.bak /mnt/etc/fstab
Then reboot. That's it.

---

### Post by mistab1034 on 2006-09-29
> **Dynapen said:**
> I have tried using the install CD and running as a live mode, but it doesn't successfully mount all the partitions, including the / partition, so I can't get at the file that way. Tried using Knoppix to do the same, still no luck. 

What do you mean it doesn't sucessfully mount all the partitions in the LiveCD? The LiveCD won't automatically mount your root partition. You'll have to manually do that:
```
mkdir /mnt/root
sudo mount -t ext3 /dev/hda# /mnt/root
cp /mnt/root/etc/fstab.bak /mnt/root/etc/fstab
```
where # is the partition number. and if you have sata then it's sda instead of hda

---

### Post by mistab1034 on 2006-09-29
oops, looks like wieman01 can type faster than me.

---

### Post by mitch.c on 2006-09-29
> **Dynapen said:**
> How can I get into some sort of rescue mode where I can have root access to cp my .bak file back into the original location of /etc/fstab?

I have tried using the install CD and running as a live mode, but it doesn't successfully mount all the partitions, including the / partition, so I can't get at the file that way. Tried using Knoppix to do the same, still no luck. 

Anyone got advice on what to try?

You don't say how your trying to mount the partition, but you should be able to use the install or knoppix cd to boot, create a directory like /mnt/ubuntu/, and then mount the hd partition that holds /etc something like this:
```
# Assumes ext3 fs and partition at /dev/hda2; edit as needed
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
```
Assuming your whole fs exists one one partition, you should be able to access /mnt/ubuntu/etc/fstab. Correct as necessary and reboot w/o cd in drive.

---

### Post by mitch.c on 2006-09-29
> **mistab1034 said:**
> oops, looks like wieman01 can type faster than me.

Ditto.

---

### Post by wieman01 on 2006-09-29
> **mitch.c said:**
> Ditto.
Looks like we're too fast for each other. ;-)

---

