---
title: "how do i access my normal system from live CD?"
date: 2009-05-16
forum: General Help
---

### Post by blue carrot on 2009-05-16
Hi guys,
I am wondering how I can access my normal directories etc. using the live CD? At the moment my system is not starting up (well, its a blank screen) when I boot from hard disk, I think it's due to a problem with xorg.conf 

I am wondering if it's possible to boot up with the live CD and then go and fix the xorg.conf file. Right now I can't see any of my old stuff (music, pictures, settings etc) when I boot with live CD. Using the 'fix X server' option in recovery mode is not currently working either. 

one thing I tried was getting into root through recovery mode and typing:

cd /etc/X11
ls

which gave me a list of all of the old backed up xorg.conf files. but i can't figure out how to replace xorg.conf with one of those files. i tried the command;

cp <xorg.conf.2009.....> <xorg.conf>

but that did not work. can anyone help me out here so that i can either 

a) replace xorg.conf with a backed up version from root in recovery mode

or

b) access xorg.conf via live cd and fix it that way somehow

---

### Post by taurus on 2009-05-16
a.  Did you use the right name when you ran the cp command?

b.  If you want to access your harddrive from Ubuntu LiveCD, you first need to mount it.  Assuming root filesystem is resided on /dev/sda1, you would do something like these from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/X11/xorg.conf
```

---

### Post by quixote on 2009-05-16
In recovery mode as root, when you gave that copy command, you didn't actually have the angle brackets around the names, right?  If you did, that was the problem.

Also, when you boot with the liveCD, if you start nautilus and have it display "Places" in the side pane, you'll see all the partitions that the system can see.  If one of those looks like the right size to be your no-longer-functioning root partition, then double-clicking will mount it.  

It will be read-only, since you started nautilus as an ordinary user.  But it'll make it easier to look through your xorg.conf backups and make sure you have the right one.

It is possible to start nautilus as root (gksu nautilus in the terminal), but be super-careful what you do.  As you know, you can really blow the system up as root. #-o

---

