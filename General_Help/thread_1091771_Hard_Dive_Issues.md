---
title: "Hard Dive Issues"
date: 2009-03-09
forum: General Help
---

### Post by LinuxN00b92 on 2009-03-09
I recently realized that my Windows XP partition was getting a bit full, so I found some old backup files that I had on both partitions and decided to delete them off of the windows partition. I'm not sure what went wrong exactly, but ubuntu and windows both still list the drive as nearly full even though the files are no longer accessible. I've tried using the native file size counters (don't know the real name, the part of the properties menu that counts up total size of all files) to see if either system recognized them, both of them will tell me that the files are gone. I also tried kdirstat and windirstat to see if I could find a recycle/trash location somewhere but they gave me even lower total used space values than the native counters. Any ideas on how to change the used space values associated with a hard disk?

I'm running 8.10 and Win XP.

Thanks in advance!:)

Note: I used ubuntu to delete the files, I don't recall it asking me at any point to empty the trash/recycle bin.

---

### Post by indytim on 2009-03-09
Try defragging a couple of passes in Windows.  Launch GParted Live and see what your partition size is.

IndyTim

---

### Post by LinuxN00b92 on 2009-03-10
I actually ran across it while looking in gparted. It says that the drive is 72 gigs. Even gparted recognizes the drive as nearly full. I tried a windows system defrag to no avail, I found a more highly recommended one at downloads.com (Auslogics Disk Defrag) its been running for like two hours and is still working, just hope its getting something done. ;)

---

### Post by LinuxN00b92 on 2009-03-10
Nope no change. :(

---

### Post by LinuxN00b92 on 2009-03-15
bump

---

### Post by LinuxN00b92 on 2009-03-22
bump

---

### Post by Liviu-Theodor on 2009-03-22
Maybe you just sent the file to the Recycle Bin (Windows) or Trash (Ubuntu). Empty them if this is the case. To delete directly the files, press the <Shift>+<Delete> keys.

---

### Post by Therion on 2009-03-22
Install QuickStart and run the "House Cleaning" option with everything checked.  I guarantee it'll free up some space for you.  Most likley your files are still in the Trash and/or root-Trash.  Quickstart is just an easy, GUI-fied way of taking out ALL the trash in one fell swoop.

[http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop)

Yes, it works for 8.10 (and 9.04 as well!) even though the article refers to the 8.04 version.

---

