---
title: "How to auto mount a drive on Start up?"
date: 2009-06-23
forum: General Help
---

### Post by luke0927 on 2009-06-23
I have a 60Gb HD that is a secondary in my box.  Its actually my windows drive that i just select in the bios when i want to boot from it.  since my ubuntu installatin is on a smaller drive I've been leaving a lot of music and things on there.  I would like that drive to auto mount when i start up so my Rythmbox music will still see the files on the other drive.

I'm about to clone and expand my ubuntu to a 160GB drive but would like to do this anyway.

would i need to create a script to run on start up or what?

its sdb1

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18543888  13128988   4480324  75% /
tmpfs                   645868         0    645868   0% /lib/init/rw
varrun                  645868       216    645652   1% /var/run
varlock                 645868         0    645868   0% /var/lock
udev                    645868      2760    643108   1% /dev
tmpfs                   645868       572    645296   1% /dev/shm
lrm                     645868      2004    643864   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sdb1             58613120  49988708   8624412  86% /media/disk

---

### Post by rbc on 2009-06-23
You need to add a line to the /etc/fstab. Here's a good how-to:
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by DeMus on 2009-06-23
Try this, it helped many people already:

**_Auto mount Windows disks_**
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by del_diablo on 2009-06-23
Install PySDM instead of ntfs-config, NTFS config lacks the config part badly.

pydsm is a gui to edit /etc/fstab, which works damn neat.

Edit: The main reason NTFS config sucks, is mainly if you got 2 disks. In my experience it will only add 1, and you cannot configure it after that.

---

### Post by 3Miro on 2009-06-23
> **del_diablo said:**
> Install PySDM instead of ntfs-config, NTFS config lacks the config part badly.

pydsm is a gui to edit /etc/fstab, which works damn neat.

Old KDE 3.x had a very nice tool to mount and unmount all partitions. At the time I was triple booting and it war great to have such a utility. KDE 4.x doesn't have one.

I hope this pydsm is good one for Gnome (that is what I am using now). (except I cannot find in the 8.10 repos)

---

