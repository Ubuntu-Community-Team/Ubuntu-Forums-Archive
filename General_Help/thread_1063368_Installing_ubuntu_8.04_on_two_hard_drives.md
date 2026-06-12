---
title: "Installing ubuntu 8.04 on two hard drives"
date: 2009-02-07
forum: General Help
---

### Post by neilevan814 on 2009-02-07
I would like to install ubuntu 8.04 64 bit version over 2 hard drives.  I would like to set the partitions up so that one partition holds the /boot one for all the directories which would be affected when I want to upgrade ubuntu to the next LTS version, I want to have a partition for /media to hold all my photos, music, movies, avi's, etc...and a partition for everything else.  Can someone, Please???, guide me in a dumby friendly way on how to set these partitions?  Thank You!

---

### Post by dcstar on 2009-02-07
> **neilevan814 said:**
> I would like to install ubuntu 8.04 64 bit version over 2 hard drives.  I would like to set the partitions up so that one partition holds the /boot one for all the directories which would be affected when I want to upgrade ubuntu to the next LTS version, I want to have a partition for /media to hold all my photos, music, movies, avi's, etc...and a partition for everything else.  Can someone, Please???, guide me in a dumby friendly way on how to set these partitions?  Thank You!

/media is already a system folder that you should **not** use for anything.

Never use existing system partitions for user files just because the name is "convenient". Always use new names that are different from system names.

---

### Post by drs305 on 2009-02-07
There are several options, but you have to create a / (called root) and swap partition.

/  -  root, the system partition, formatted to ext3 (10-15 GB)

swap - the swap partition, formatted as swap, generally 1-2x your memory

data - for your media. I would ***not*** call it *media*, as ubuntu creates a special mount point called *media* as a directory for mounting removable drives and other devices.

/home  - optional, formatted as ext3.  Some people like to have a separate /home so when they upgrade to a new version their configuration settings are preserved if they do a clean install (or reinstall). If you don't have a separate /home partition, you would be able to do an upgrade to a newer version and retain your settings. You could not do a clean install and keep them without special effort. Many users keep most of their data in /home, while others keep /home mostly for their configuration settings and have other partitions for their data.

I'd recommend setting up the partitions before starting the installation by booting to with the ubuntu LiveCD and then using the ubuntu default partition editor, *gparted*. You access it via System, Administration, Partition Editor. Once you have created a partition setup to your liking, start the installation and select *manual* partitioning.

Here is a thoughtful discussion of how to set up an installation:
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

---

### Post by neilevan814 on 2009-02-07
Okay, thank you both for your comments.  I will definitely NOT call a partition media...no no no...So, from what I gather on the other site, I do not need to actually create a separate boot partition?  If someone could give me a how to on how they would set up a two drive ubuntu system that has easy updatability for future LTS's with a separate partition for /home and one for /stuff(aka media) and one for /swap and one for /boot I would be forever grateful.  Tell me where I need to put flags on the partitions and stuff like that too...and how large the partitions should be if I had say 100 Gb's of stuff to store.

Thanks again, Neil

---

### Post by castawaybcn on 2009-02-07
not sure if this will help, but you may want to have your home partition in a different drive, so that you can upgrade to the next ubuntu version without losing your configuration files and data. Take a look at these tutorials:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/ ]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by neilevan814 on 2009-02-07
Alright, yes I have been reading these and they do help.  Now here is a question for a system I would like to upgrade my motherboard and processor on.  If I wanted to ensure that my LAMP configuration was not lost or any of my document files and music files and ssh keys...Would moving my home directory to a new partition on the current drive salvage all my settings and would I then be able to reinstall ubuntu for the new hardware board as just a / partition?  And if this does work...Wouldn't I have to rewrite file paths for some of the conf files for the LAMP??

Forever learning..Thanks,Neil

---

### Post by neilevan814 on 2009-02-07
Okay from re-reading the move /home partition tutorial, I see that in modifying the /etc/fstab file it will automatically read the new partition as /home...so all should be preserved then right????  I'm not forgetting anything, right?  I did a basic install originally on that machine so no added partitions or special folders created.

---

