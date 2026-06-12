---
title: "Acessing Windows hard drive from A live Flash"
date: 2009-06-19
forum: General Help
---

### Post by Hatman13 on 2009-06-19
Hey guys, (and gals)

I am currently having problems with my windows laptop, and i have a Ubuntu 8.10 installed on a flash drive.  

My Windows has become corrupted and i cannot access any files int it, or even boot into it, let alone safe mode.  So for the last week i have been running Ubuntu persistently  as a way to use my computer.  I am trying to access files on my computer but i am unable to mount the hard drive.  I have not been able to find any way of getting to these files, i know there is a way if you can access the terminal but i cannot access the terminal yet. 


Any help would be greatly appreciated.

---

### Post by asmoore82 on 2009-06-19
to gather information on drives and partitions:
```
sudo fdisk -l
```

---

### Post by Hatman13 on 2009-06-21
> **asmoore82 said:**
> to gather information on drives and partitions:
```
sudo fdisk -l
```


So this got me the info for the drive, when i enter 

/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
Into the terminal this is the response i get:

bash: /dev/sda1: Permission denied

Any more advice?

---

### Post by aduhot1 on 2009-06-21
> **Hatman13 said:**
> Hey guys, (and gals)
 
I am currently having problems with my windows laptop, and i have a Ubuntu 8.10 installed on a flash drive. 
 
My Windows has become corrupted and i cannot access any files int it, or even boot into it, let alone safe mode. So for the last week i have been running Ubuntu persistently as a way to use my computer. I am trying to access files on my computer but i am unable to mount the hard drive. I have not been able to find any way of getting to these files, i know there is a way if you can access the terminal but i cannot access the terminal yet. 
 
 
Any help would be greatly appreciated.
:popcorn:Bumping....
[img]http://www.snagpic.com/users/img/4092/n09x0302vnsn/clear.gif[/img]

---

