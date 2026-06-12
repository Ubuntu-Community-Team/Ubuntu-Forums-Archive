---
title: "Is it possible to resize the root partition to allow space for swap?"
date: 2007-05-15
forum: Desktop Environments
---

### Post by kostovnet on 2007-05-15
I've installed Feisty before it was officially released but it's now up-to-date :) of course. 

Back then there was some problem with the build-in partitioner so during setup I was unable to create a swap partition - I have 1 GB RAM so it was acceptable at the time to go without it.

Now I'd like to know if there is a way to resize the partition mounted as root in order to free up some disk space, to create a linux swap partition and then how to make it usable by Feisty ?

Currently, Feisty is on my hda5 partition, formated as ext3 - size: 15GB, free space: 3.7GB, I'd like to have ~0.7GB of swap available.

All other partitions are NTFS.

---

### Post by heimo on 2007-05-15
My suggestion - make a swapfile.
[http://ubuntuforums.org/showpost.php?p=287528&postcount=6](http://ubuntuforums.org/showpost.php?p=287528&postcount=6)

---

