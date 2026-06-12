---
title: "gnome doesn't start"
date: 2008-08-03
forum: Desktop Environments
---

### Post by dersu on 2008-08-03
Hi,
I am a newbie on linux.
I have hardy on my dell inspiron 1300.
everything was working.
but trying compiling xmms and some kind of messenger, I think I did bad things, and now gnome doesnT work.
It starts, I have mybackground image and that's all.
I started in text mode, installed fluxbox, and I am using it now.
But how I will fix my gnome, I dont know where the problem is.
or how I can reinstall it.
Thanks in advance.

---

### Post by phidia on 2008-08-03
You say gnome starts but you don't have any panels? Is that what you meant by this:> It starts, I have mybackground image and that's all.?

You might have messed up some configuration files in your home directory.
You could create a test user "sudo adduser test" and see if test can login using Gnome.

If you really want to reinstall Gnome > sudo apt-get install --reinstall ubuntu-desktop could do that but it will be a lot of packages.

---

### Post by dersu on 2008-08-03
Thanks
I added a new user (IT was a smart idea), but nothing changed.
So I tried:
sudo apt-get install --reinstall ubuntu-desktop 
But it has processed with one package and the situation doesn't change.
Now I try to backup my data, but I can't mound my external hard disk.

Thanks.

---

### Post by phidia on 2008-08-03
> **dersu said:**
> Thanks
I added a new user (IT was a smart idea), but nothing changed.
So I tried:
sudo apt-get install --reinstall ubuntu-desktop 
But it has processed with one package and the situation doesn't change.
Now I try to backup my data, but I can't mound my external hard disk.

Thanks.

Is your external hard drive usb? in terminal enter "sudo fdisk -l"
From that you should be able to locate the partition(s) your external drive has.
So then create a mount point "sudo mkdir /mnt/extdrive (choose any name you want after "/mnt" 
To mount the drive enter: "sudo mount /dev/sdb1 /mnt/extdrive"
I used sdb1 but it might be sdg1 or something else. You will need to use the actual partiton you found from fdisk -l.

---

### Post by dersu on 2008-08-03
thank you a lot

---

