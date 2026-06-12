---
title: "shared partitions"
date: 2004-12-10
forum: Desktop Environments
---

### Post by M@t on 2004-12-10
I am going to redefine partitions on my main harddisk. I plan to have 3 slots for linux distributions, one for hoary, one for warty to be able to work if I break my hoary and a third one to test other distributions.

 1st slot   /dev/hda1   *      Linux
 2nd slot  /dev/hda2           Linux
 3rd slot   /dev/hda3           Linux
                /dev/hda4           Extended
                /dev/hda5           Linux swap / Solaris
 data        /dev/hda6           Linux

I think I am going to avoid to share my home partition to avoid conflicts in configuration files. Therefore, I would like to have all the files of my data partition available in the /home/user/ directory for each distribution. So, is it possible to have the content of hda6 directly available in /home/user/ or do I have to mount hda6 in a subfolder, eg /home/user/data/ ?

---

### Post by adbak on 2004-12-10
Do you think it'd be possible for you to share your home folder but use a different user name for each of the distros that you'll try?  Like Matt for Warty, Matthew for Hoary, Matt [surname] for any other one?

Edit:  rereading what you wrote it seems to me like that may be what you just said....

---

