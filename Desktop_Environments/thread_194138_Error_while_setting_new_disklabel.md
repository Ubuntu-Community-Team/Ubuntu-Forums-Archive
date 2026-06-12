---
title: "Error while setting new disklabel"
date: 2006-06-11
forum: Desktop Environments
---

### Post by triPzZz on 2006-06-11
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11032&stc=1&d=1150001848[/IMG]

Any help is greatly appreciated.  I am just trying to create a disklabel on my hard drive..however, when I installed ubuntu the install seemed to go through alright, having the install create the partitions.  When I restart now, it stops at "Error 18".  I've found in a thread that someone said to try and reinstall, but when I do, the process more or less repeats itself, error 18, and I can't create a disklabel.  Thanks!

---

### Post by Rui Pais on 2006-06-11
hi,
do you tried to simply create a pimary partition on HD? 
It should done all needed automatically.

Or, if its really need to create a disklabel, maybe there is a bug on gparted (maybe?), try to do it from the command line, with
```
sudo fdisk /dev/hda
```
It's the "o" option, ithink, you need to use.

hth

---

### Post by triPzZz on 2006-06-11
Thx for your reply, unfortunately I am only getting the following:

Unable to read /dev/hda

---

### Post by Rui Pais on 2006-06-11
hi,
it says that it can't read from hda when you try to access form a livecd or an installcd?

Strange... Do you any other drive connect to that IDE. They are correctly set as master/slave?

---

