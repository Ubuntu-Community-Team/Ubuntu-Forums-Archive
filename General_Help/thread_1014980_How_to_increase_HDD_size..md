---
title: "How to increase HDD size."
date: 2008-12-18
forum: General Help
---

### Post by User_X on 2008-12-18
I have installed ubuntu 2 days ago from windows_XP on a 30gb fat32 partition, without burning a disk.

During installation i have selected 20GB 
  [IMG]http://www.freewaregenius.com/wp-content/uploads/2008/05/ubuntu-setup.jpg[/IMG]

Screen where i have selected the part. size (I Got it frm net just to give an idea what i did)

Now on my 30GB drive where ubuntu is installed I have about 16GB free. but for ubuntu in disk folder i have

Total size of disk folder is 12GB
Home.disk = 3.72 GB
Root.disk = 3.72 GB
swap.disk = 953 MB
usr.disk = 3.72 GB

IN ubuntu whenever i try to copy a file over 5gb on the desktop, an error comes up saying i have only 3.72gb space on the disk, and file could not be copied.

How do i increase the size of the partition, so that i can copy that file on the Ubuntu desktop.

---

### Post by User_X on 2008-12-18
so am i suppose to increase the size of usr.disk???????????

---

### Post by albinootje on 2008-12-18
> **User_X said:**
> 
Total size of disk folder is 12GB
Home.disk = 3.72 GB
Root.disk = 3.72 GB
swap.disk = 953 MB
usr.disk = 3.72 GB

IN ubuntu whenever i try to copy a file over 5gb on the desktop, an error comes up saying i have only 3.72gb space on the disk, and file could not be copied.

Your desktop is in /home so that error message makes sense.

You're using Wubi i assume, i don't know whether you can run gparted inside Wubi.
I suggest doing a search-engine search for "wubi gparted".

---

### Post by User_X on 2008-12-18
> **albinootje said:**
> Your desktop is in /home so that error message makes sense.

You're using Wubi i assume, i don't know whether you can run gparted inside Wubi.
I suggest doing a search-engine search for "wubi gparted".


Oh... okey,, so i will first increase the size of home.disk, 

but gparted is linux app, will it be able to increase the size of running partition..? 

or should i use some live disk? but again linux disks are in FAT32 partition just as files, will i be able to see them even if I use some kind of disk manager...??

---

### Post by albinootje on 2008-12-18
> **User_X said:**
> Oh... okey,, so i will first increase the size of home.disk, 

but gparted is linux app, will it be able to increase the size of running partition..? 

or should i use some live disk? but again linux disks are in FAT32 partition just as files, will i be able to see them even if I use some kind of disk manager...??

I have no experience with Wubi, but why not try whether gparted will be able to resize your /home partition in Wubi ?

---

### Post by vanadium on 2008-12-18
I do not recommend you to resize your wubi install. Doing so will take space away from your Windows install.

A better option is to use the available space under Windows from within Ubuntu. This can conveniently be achieved by symbolic links in your Ubuntu home directory that redirect you to space on your Windows C drive. That way, your ubuntu drive can remain small, while you still have all space you need.

I am pretty sure you also can link Desktop to the Windows partition so that you could put gigabyte files on your desktop (I don't know if that is good organisation, though).

If interested, ask detail if needed.

---

### Post by User_X on 2008-12-18
thank you so much,, but I changed my mind,

now i am going to add a hdd, will duel boot this time,

and i have tested that live disk but as i assumed it didnt worked, however i will play around with some iso editor.. 
coz. Hear i am dealing with a file in file system.

---

### Post by ago on 2008-12-19
yes, if you find you need more space it is probably a sign that you have to install to a dedicated partition.

Anyway you cannot have files larger of 4GB in fat

---

### Post by User_X on 2008-12-19
> **ago said:**
> yes, if you find you need more space it is probably a sign that you have to install to a dedicated partition.

Anyway you cannot have files larger of 4GB in fat

never thought of it..#-o
anyways i am going to convert it to ntfs

---

