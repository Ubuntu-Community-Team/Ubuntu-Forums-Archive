---
title: "Partition Icons on Desktop"
date: 2007-02-19
forum: Desktop Environments
---

### Post by cornellpd on 2007-02-19
I just reinstalled Ubuntu, set the default boot to Windows for my wife-(with the help of some fine people over on the beginner page)-and now I see that I have 3 Icons-look like Hard Drive Icons- on my desktop.  One is Dell Restore, One is Dell Utility, and the there is sda2.  These are all hard drive partitions in my hard drive.  I could not set up more than 4 Primary Partitions while installing Ubuntu, so I created an extended partition after windows partition, and then proceeded to install Ubuntu on a couple of other partitions after that.  Is it possible to remove these icons without hurting the XP installations-and if so, how?  Thanks.

I tried to unmount them, and am unable to:  "unmount: only root can unmount /dev/sda4 from /media/sda4"

How do I become "root" ?  I am the administrator-I figure I have to log in, and then go to a terminal and somehow change to root?

They are also under "places" tab, with desktop and everything else.

---

### Post by jhorner on 2007-02-19
> **cornellpd said:**
> I just reinstalled Ubuntu, set the default boot to Windows for my wife-(with the help of some fine people over on the beginner page)-and now I see that I have 3 Icons-look like Hard Drive Icons- on my desktop.  One is Dell Restore, One is Dell Utility, and the there is sda2.  These are all hard drive partitions in my hard drive.  I could not set up more than 4 Primary Partitions while installing Ubuntu, so I created an extended partition after windows partition, and then proceeded to install Ubuntu on a couple of other partitions after that.  Is it possible to remove these icons without hurting the XP installations-and if so, how?  Thanks.

I tried to unmount them, and am unable to:  "unmount: only root can unmount /dev/sda4 from /media/sda4"

How do I become "root" ?  I am the administrator-I figure I have to log in, and then go to a terminal and somehow change to root?

They are also under "places" tab, with desktop and everything else.

In terminal, try ```
sudo umount /media/sda4/
```

---

### Post by Rippey on 2007-02-19
to unmount the drive use this command in a terminal "sudo umount /dev/sda4".
this will unmount the drive but it'll be back the next time you boot, to stop ubuntu from mounting your drives, edit your fstab file. you do that by typing "gksu gedit /etc/fstab" comment out (place a # in front of the line) all drives you don't want mounted at boot time and save the file, be carefull though, if fstab gets damaged you might not be able to boot ubuntu.

---

### Post by cornellpd on 2007-02-19
Thanks Jhorner-that does the trick to get rid of them, but when I restart-they come back.  They must be in my startup settings/config?  What can I do to keep them off at restart?

---

### Post by y0ssarian on 2007-03-19
in a terminal type:
```
gconf-editor
```
then select apps > nautilus >desktop and uncheck volumes_visible

---

