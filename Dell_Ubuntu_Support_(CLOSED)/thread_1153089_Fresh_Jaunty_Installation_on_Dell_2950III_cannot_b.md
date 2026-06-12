---
title: "Fresh Jaunty Installation on Dell 2950III cannot boot"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jinzishuai on 2009-05-08
Hi there,

I just got a new Dell 2950 III and tried to install Jaunty on it. The installation process went smoothly. But when I boot the machine from harddisk, I got the error saying that the root device is not found. I tried to do it manually, with different partition method such  as LVM. None of the works. 

In the shell I was dropped to, I can see the the /dev/*** device file that is said not found is actually right there.
I also tried both the desktop and server version (both AMD 64) and the problem is the same.

I am totally disappointed. I don't know whether it it because I am having a new DELL machine. 

If anyone could shine some light on this issue, I am deeply grateful.
Thanks a lot.

Shi

---

### Post by milton1 on 2009-05-08
Do you get this message from GRUB, or after linux starts to boot? Can you give us the exact error message?

---

### Post by wgarider on 2009-05-08
> **jinzishuai said:**
> Hi there,

I just got a new Dell 2950 III and tried to install Jaunty on it. The installation process went smoothly. But when I boot the machine from harddisk, I got the error saying that the root device is not found. I tried to do it manually, with different partition method such  as LVM. None of the works. 

In the shell I was dropped to, I can see the the /dev/*** device file that is said not found is actually right there.
I also tried both the desktop and server version (both AMD 64) and the problem is the same.

Shi

Do you have a PERC RAID controller on the server or are you booting off a single, direct attached disk?

---

### Post by jinzishuai on 2009-05-10
> **milton1 said:**
> Do you get this message from GRUB, or after linux starts to boot? Can you give us the exact error message?
Thanks milton1.
I got the message after grub boots and I actually saw the Ubuntu graphics for a while and then it dropped to a shell.

---

### Post by jinzishuai on 2009-05-10
> **wgarider said:**
> Do you have a PERC RAID controller on the server or are you booting off a single, direct attached disk?
Thanks wgarider.
I do have a PERC RAID controller on the server and the two disks shows up as one drive to the OS. Is this a problem to Jaunty?
I have installed almost all the other distributions on this machine and Ubuntu is the only one with a problem. 

Thanks a lot.

---

### Post by wgarider on 2009-05-10
> **jinzishuai said:**
> Thanks wgarider.
I do have a PERC RAID controller on the server and the two disks shows up as one drive to the OS. Is this a problem to Jaunty?
I have installed almost all the other distributions on this machine and Ubuntu is the only one with a problem. 

Thanks a lot.

So if you have a PERC controller, a couple of questions....one, did you make all the disks one logical volume? If so, did Ubuntu show the correct size for that volume?

Just curious......did you try a previous version of Ubuntu on this server?

---

### Post by jinzishuai on 2009-05-19
Thank you.

I just tried to disable to the RAID 1 setup in the SAS controller so that I am having simply two 450GB SAS drives. Then I tried to install the Januty again. However, the same problem happened.
I got
> 
Gave up waiting for root device. 
...
ALERT! /dev/disk/by-uuid/01xxxxx-d3 does not exist. Dropping to a shell!

BusyBox v1.10.2 (....)
...
(initramfs) cd /dev/disk/by-uuid
(initramfs) ls
49xxxx6f 01xxxxd3
bbxxxxf1 29xxxxd5

So apparently something is wrong in terms of finding the drive but I do have the drive in the initramfs shell.

Anyone know what is going on here?
Thank you.

---

### Post by jinzishuai on 2009-05-19
OK. Problem solved.

1. When I type exit in the initramfs shell, the boot process continues and everything is normal again.

2. Then I thought it is just not enough time to find the drive. So I put "rootdelay=200" in the grub and then the whole thing worked. As how much delay is needed, I am not sure. I tried 10 but it didn't work while 200 worked. 

Hope this can be helpful for anyone with similar experience and I thank everyone who shared their thoughts.

Shi

---

