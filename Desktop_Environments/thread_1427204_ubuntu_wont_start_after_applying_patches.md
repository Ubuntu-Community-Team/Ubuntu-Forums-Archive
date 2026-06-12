---
title: "ubuntu wont start after applying patches"
date: 2010-03-11
forum: Desktop Environments
---

### Post by unix1adm on 2010-03-11
I just loaded ubuntu 9.10 on my laptop. Toshiba it loaded fine. So I ran update on the system and it updated to teh 9.20 kernel (dont remember act numbers)

But now it wont reboot.

I get udevadm trigger is not permitted while udev is inconfigured
udev settle is not permitted while udev is unconfigured
svgalib: Cannot open /dev/mem
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait long enought for device?)
- Missing modules (cat /proc modules; ls /dev)
ALERT! /dev/disk/by-uuid/e1768deb-95e0-44bd-96b0-b725c73d42af does not exist. Dropping to a shell

Busy box v.1.13.3 (Ubuntu 1:1.1.13.3-1ubuntu7) built in shell (ash)
Enter help for a list of built-in commands
(initranfs)

edit:

Kernel 2.6.31-20-generic.

It had
kernel 2.6.31-14-generic

I was able to boot back into the old kernel.. so whats happening? why wont the upgraded kernel work?

---

### Post by tom4everitt on 2010-03-11
Thats why we have backup kernels :) 

What is the output of 

```

file /dev/disk/by-uuid/e1768deb-95e0-44bd-96b0-b725c73d42af

```

if it is something like: device does not exist, you can try running:

```

sudo update-grub

```

as there seems to be something wrong with your /boot/grub/grub.cfg.

If it does exist there seems to be something wrong with your kernel, and you could try:

```

sudo apt-get reinstall linux-image-2.6.31-20-generic

```

---

### Post by unix1adm on 2010-03-11
I am guessing you do this from the old kernel since the new one wont boot.

---

### Post by tom4everitt on 2010-03-11
Yes, do it from the old kernel. That will work fine.

---

### Post by unix1adm on 2010-03-13
sudo update-grub did not do much. 

so i ran these commands and it told me the file did not exist.

file /dev/disk/by-uuid/e1768deb-95e0-44bd-96b0-b725c73d42af

I ran the update command  and it told me there was an issue some of the openoffice sw and some other stuff.

sudo apt-get reinstall linux-image-2.6.31-20-generic gave an error.. 

The process told me to run this command....
sudo dpkg --configure -a

Once I did that I ran the update kernel command listed above and it said not needed or some such message.

I rebooted and things are working now.

So the problem looks like it was with openoffice and some java sw. 
Sorry i dont have the actual errors I did not think to save them before the reboot. 

Hope this helps someone else if they run into it.

---

### Post by unix1adm on 2010-03-23
so i had this issue again on another system. the system was not updated and was working fine then it locked up and the monitor went bonkers. 

Now i get this

apt-get --reinstall linux-image-2.6.31-20-generic
E: Invalid operation linux-image-2.6.31-20-generic


Thoughts???

---

### Post by tom4everitt on 2010-03-23
Yes, try:

sudo apt-get remove --purge linux-image-2.6.31-20-genereic
sudo apt-get install linux-image-2.6.31-20-genereic



It seems like it doesn't like the --reinstall. Maybe it should have read:

apt-get install --reinstall linux-image-2.6.31-20-generic

or something, I'm not quite sure. The top version should work anyhow.

---

### Post by unix1adm on 2010-03-24
> **tom4everitt said:**
> Yes, try:

sudo apt-get remove --purge linux-image-2.6.31-20-genereic
sudo apt-get install linux-image-2.6.31-20-genereic



It seems like it doesn't like the --reinstall. Maybe it should have read:

apt-get install --reinstall linux-image-2.6.31-20-generic

or something, I'm not quite sure. The top version should work anyhow.

the command worked now to see if that resolves my issue

---

