---
title: "0 bytes left on device while 2.5 Gb are free"
date: 2009-03-17
forum: General Help
---

### Post by P4VV37 on 2009-03-17
This is all happening after resizing /home ext3 partiton.
Nautilus shows that I have no free space left, while I know I've got some. gparted shows that I've got more then 2.5 Gb space left.

"/" partition has got space left and nautyilus shows it.

System, specialy firefox and amarok, is very unstable. 

I've checked partition from live cd, using gparted, but there are no errors.

How to fix it?

P.s.
Sorry for my english :oops:

---

### Post by taurus on 2009-03-17
Can you boot into recovery mode from GRUB menu and drop into root shell?  Then, post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by solitaire on 2009-03-17
How big is your drive?
Ubuntu keeps 5% of each partition in reserve for Root (so that the drive can't get 100% full and fail to start up.)

You should increase the size of your /home partition.. (or backup and archive some of your data in your)

---

### Post by Slim Odds on 2009-03-17
> **solitaire said:**
> How big is your drive?
Ubuntu keeps 5% of each partition in reserve for Root (so that the drive can't get 100% full and fail to start up.)

And 5% can be way too much depending on the size of the partition. I recommend making it less....

man tune2fs

Also note that for your home partition, you probably don't need **any** reserved space.....

---

### Post by P4VV37 on 2009-03-17
Thanks
This partition is 100 Gb.
I deleted more files, now I've got more then 5 Gb of free space, and nautilus show that I have 700 Mb.

there are a lot of options in

man tune2fs

Can You tell me what exacly should I do?

---

### Post by Slim Odds on 2009-03-17
> **P4VV37 said:**
> 
man tune2fs

Can You tell me what exacly should I do?

```
sudo tune2fs -m 1 /dev/sd??
```That would be a start.....

---

### Post by valros on 2009-03-17
Somewhat related, why do file operations show the my home directory as having a couple gigs more stuff than it does, for example my home directory shows 30gigs from the properties of the folder, however when copying it the file operation window will sound out "Preparing to copy 60gigs". Is it also copying linked files or is this a bug?

---

