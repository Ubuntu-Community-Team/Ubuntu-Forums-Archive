---
title: "Mount Drives to Folders That Contain Data?"
date: 2009-05-18
forum: General Help
---

### Post by sablefoxx on 2009-05-18
So basically current setup for my media server is a 1Tb drive that contains all my data, however i am running out of space (blu-ray rips add up).  So i bought i second 1Tb drive and would like to mount it to /home/user/Videos but there is about 800Gb of data already there so my questions are:

1. How do i mount the drive /home/user/Videos, without loosing any of the data? (sudo mount /dev/sda1 /home/user/Videos  works but then i cannot access the data on sdb)

2. Do i edit the fstab file so sda1 gets mounted every time i boot the system, if so how?  (and how do i remove the icon from the desktop for the second drive)

3. Do i need to fix permissions on the new drive?  and what permissions should i use? 775?

4. What is the Lost & Found folder for?

---

### Post by quixote on 2009-05-18
lost+found is a system folder which you shouldn't change.

Mounting a partition to a place that already has data does nothing to the existing data.  When you unmount the new partition, the old data is right there.  But there's no way to mount the new partition "next to" the old data, as it were.  You can't see both at the same time.  Changing permissions, and so on, won't alter that.

You could mount your new partition to /home/user/Videos2

If you want to have everything appear in one directory, I'm not sure what your options are.  Maybe there's an elegant solution using symlinks.

The way I use it, it's all still in its own directory:
```
ln -s /mnt/data/pics /home/user/pics
```
makes all the photos in my media storage (mounted on /mnt/data) appear as if they're part of my /home without actually taking up space there.

---

### Post by HermanAB on 2009-05-19
Howdy,

You have to mount a share onto a subdirectory and that subdirectory should be empty.  If you need the files inside another subdirectory, then you need to make soft links to them.  That is usually too much effort.

The other way is to use the Logical Volume Manager to graft things together.  That is even more useless effort.

So, just mount your shares onto a subdirectory like everybody else does.

---

### Post by gamblor01 on 2009-05-19
[quote=sablefoxx]
 (and how do i remove the icon from the desktop for the second drive)
[/quote]

Simple if you're using gnome.  Just run the following command:

```
gconf-editor
```

Then click on apps -> nautilus -> desktop. There should be an option in there that says "volumes_visible". Just remove the checkbox from there and it should hide the mounted volume(s) on your desktop.

---

### Post by sablefoxx on 2009-05-20
thanks for the help guys, just wanted to make sure i wasnt doing it wrong

---

