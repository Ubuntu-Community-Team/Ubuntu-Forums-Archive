---
title: "Need brain-dead simple disk imaging steps"
date: 2006-03-02
forum: Desktop Environments
---

### Post by JackD on 2006-03-02
I'm supporting a computer lab for an orphange in Nairobi ([http://www.nyumbani.org)](http://www.nyumbani.org)). I've installed Edubuntu on a number of systems, would desperately need to simplify the entire process by creating an image of Edubuntu on a couple of CDs and installing from those CDs.

--I've tried Ghost 2003, but it hasn't been reliable. There are *lots* of switches that might or might not help, but I can't find any guidelines.

- I've tried partimage, but am having bad luck. 

 a. I've partitioned a drive into 
       -hda1 which is root and holds the Edubuntu installation
       -hda2 the swap file
       -hda3 an ext2 for storing a partimage file

 b. I've tried booting into partimage from Knoppix or Helix, but I'm not able to create a file onto hda3.

I've looked through the forum, but could not identify any step-by-step guidelines

---

### Post by Almighty on 2006-03-02
I stumbled on this software a while ago but never got around to trying it out. Maybe you can test it and see how it works out for you. [http://freshmeat.net/projects/g4l/]("http://freshmeat.net/projects/g4l/"). Its an application similar to Symantecs Norton Ghost.

---

### Post by glug101 on 2006-03-02
Let us know how well it works if you can.  I plan on using the same software in a similar situation.

---

### Post by queenorych on 2006-03-02
Could try mondo to backup. 

If that doesn't work just boot up a live cd and use good old 
dd if=/dev/hda of=/mountpount-of-networked-machine/backup

then restore of=/mountpount-of-networked-machine/backup if=/dev/hda 

You can use gparted to grow partitions if you have different size disks.

---

