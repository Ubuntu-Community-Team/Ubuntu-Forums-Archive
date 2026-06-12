---
title: "home folder questions"
date: 2009-08-17
forum: Desktop Environments
---

### Post by thundaraptor on 2009-08-17
I have two partitions on a 1 tb hdd.  The first partition is 25 gb and has the jaunty jackelope build that I am currently using.  The second 975 gb partition has all my data, in the home folder of a jaunty build that I messed up pretty badly.  All the data is there/intact and I have a backup of it but I want to know how to

(1) get all the data out of the home folder some way other than copying it as 400 gb is a slow copy

and 

(2) how do I completely remove the jaunty install from that partition so that the partition is empty and can be used only as a place to store information.  ie, no executables and no system files.  

thanks,

TR

---

### Post by mcduck on 2009-08-17
1. The only way to copy data is to copy data.. :D

2. Use any partition editor to format the partition into file system you'd like it to be. Gparted, fo example, is pretty good, simple to install in Ubuntu and also available by default on Ubuntu's live-CD's.

---

### Post by asmoore82 on 2009-08-17
It sounds like all you need to do is delete every folder on the 2nd partition except home;
*then move everything in home up a level;
*then remove home;
and finally set that 2nd partition to mount to /home on your main install.

* - shown here:
```
mv home/* ./
rmdir home
```

simply moving folders around on the same partition should be almost instant -
a mere "book-keeping" operation as opposed to actually copying data.

---

