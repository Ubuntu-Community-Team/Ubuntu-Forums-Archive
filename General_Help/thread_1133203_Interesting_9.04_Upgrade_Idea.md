---
title: "Interesting 9.04 Upgrade Idea"
date: 2009-04-22
forum: General Help
---

### Post by Dr Belka on 2009-04-22
So I am going to be upgrading to Jaunty when it comes out.  I would just do clean installs on all of my computers, but I am hesitant about bugs and such plaguing me.  

As you know, Ubuntu is installed in an extended partition with one part ext3 file system and one part swap space.  I would like to install Jaunty in the extended partition alongside Intrepid, using the same swap space both being listed in the grub boot menu.  Does anyone know how I might go about doing this, or if it is even possible/practical?  I have an idea how to do it, but the shared swap space would baffle me a bit.

After awhile of testing the Jaunty release and its stability, I will delete the Intrepid Partition and pretty much just move a couple things into its place.


Any thoughts?

---

### Post by DagMan on 2009-04-23
You can't install two operating systems to the same partition.  
You can install two operating systems to 2 partitions, one on each partition, and only have one swap partition in addition.

---

### Post by Dr Belka on 2009-04-27
Actually, it worked... I just dropped it in another section of the ubuntu extended partition

---

