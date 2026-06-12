---
title: "Can I reinstall Dapper leaving home intact?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by mister_p_1998 on 2006-09-04
My 11 year old som managed to trash his two week old install of Dapper (although to be fair, it could be an iffy drive) , can I reinstall without wiping the home dir?

---

### Post by OffHand on 2006-09-04
In short yes.
You will have to give the partitions mount points but DO NOT ERASE what is on them.

---

### Post by hexion on 2006-09-04
Offhand, if he does that there will be a lot of trash in his system... he wants to keep only his /home directory

The easiest way is this:

- Boot with a live cd (the same CD you have to install ubuntu
- Open a terminal
( I will asume your system was mounted in /dev/hda2, change this if it's different)
> sudo -s
mkdir MYSYSTEM
mount /dev/hda2 MYSYSTEM
cd MYSYSTEM
mkdir OLD
mv * OLD
mv OLD/home .
cd ..
umount MYSYSTEM 
Then, reinstall ubuntu and choose DO NOT FORMAT the partition.

When everything is OK (or just before installing the system if you have fewer space), you can delete your old files by typing:
> sudo rm -r /OLD

---

### Post by OffHand on 2006-09-04
> **hexion said:**
> Offhand, if he does that there will be a lot of trash in his system... he wants to keep only his /home directory

The easiest way is this:

- Boot with a live cd (the same CD you have to install ubuntu
- Open a terminal
( I will asume your system was mounted in /dev/hda2, change this if it's different)
 
Then, reinstall ubuntu and choose DO NOT FORMAT the partition.

When everything is OK (or just before installing the system if you have fewer space), you can delete your old files by typing:

Sorry dude but what I say is right. Only erase the / and set the mount points on the others (but not erase them) is a good method. Your method might work aswell, I don't know.

---

### Post by hexion on 2006-09-04
I must disagree :)
If he installs his new system above the old, he'll get many trash-files in the way.

In example:
There are files in /etc/rcS.d  those are links to programs, and are loaded at boot time.
If he does what you do, those files will stay there but they can reffer on programs that are no longer installed in the new system, and may have problems.

Another example:
apt-get , aptitude, and dpkg mantains a list of installed packages.
All the programs he had installed in his old systems will remain in /usr/bin and so... but he will not be able to uninstall them because aptitude, apt-get, and dpkg will tell they are not installed.

Apart of possible problems, there will be a lot of space wasted of files left there with no use.

But, of course, I might be wrong ;)

---

### Post by OffHand on 2006-09-05
> **hexion said:**
> I must disagree :)
If he installs his new system above the old, he'll get many trash-files in the way.

In example:
There are files in /etc/rcS.d  those are links to programs, and are loaded at boot time.
If he does what you do, those files will stay there but they can reffer on programs that are no longer installed in the new system, and may have problems.

Another example:
apt-get , aptitude, and dpkg mantains a list of installed packages.
All the programs he had installed in his old systems will remain in /usr/bin and so... but he will not be able to uninstall them because aptitude, apt-get, and dpkg will tell they are not installed.

Apart of possible problems, there will be a lot of space wasted of files left there with no use.

But, of course, I might be wrong ;)
Read again  ;)

---

### Post by facefur on 2006-09-05
As long as you created a /home partition for the original install, the reinstall should be simple.  

Having personally done a reinstall or upgrade on two machines, I can say that the simplest method is to do a fresh install from the Install CD.  Please use the Alternative CD, as it seems to be the only reliable one around, using the "Text Install" choice.  Assuming no other changes, when you reach the partition step, simply create mount points for each partition, and do NOT reformat your original */home* partition.  This will replace all the files, but leave your personal stuff intact. I wrote down the old mount point names before I began.

If you are paranoid (sometimes a good thing) you might want to back up that */home* partition to a DVD or CD before you start.

---

### Post by alecjw on 2006-09-05
Just select "Rescue a broken system" in the boot menu on the CD?

---

