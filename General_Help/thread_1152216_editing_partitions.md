---
title: "editing partitions"
date: 2009-05-07
forum: General Help
---

### Post by suicidal pencil on 2009-05-07
Hello, world!

I'm relatively new to the Linux world, so please excuse my naivety and ignorance. 

I'm dual booting Windows and Ubuntu on only an 80GB hard drive, and I gave Windows 21GB to play with, and 59GB to Ubuntu. I'm trying to give more space for windows to play with since for what I'm doing, Ubuntu does not need as much space as I gave it. I've already tried using *Parted* to edit the partitions, but it apparently does not support NTFS file systems. This is what I've come across using *Parted*:

```

suicidalpencil@suicidalpencil-desktop:~$ sudo parted
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) resize                                                           
Partition number? 1                                                       
Start?  [32.3kB]? 32.3kB                                                  
End?  [21.0GB]? 31GB                                                      
No Implementation: Support for opening ntfs file systems is not implemented yet.

(parted) 

```Is there anything that I could do to increase the amount of space Windows can use? (I'm using windows for gaming, and Ubuntu for my programming work.)

---

### Post by taurus on 2009-05-07
You MUST use gparted from either Ubuntu LiveCD (System -> Administration -> Partition Editor) or GParted LiveCD.  You cannot resize a partition while you are using it.  

Always back up your files first.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by suicidal pencil on 2009-05-07
ok, so I'll toss my CD in and mess with it. Thanks a bunch!

---

