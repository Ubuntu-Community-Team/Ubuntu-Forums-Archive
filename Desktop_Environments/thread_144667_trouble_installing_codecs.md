---
title: "trouble installing codecs"
date: 2006-03-14
forum: Desktop Environments
---

### Post by terranz on 2006-03-14
I was following instructions here [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

and tried to get some codecs and got this output as typical
> gerard@terranz:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backpor ts_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-b ackports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-bac kports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/ multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-b ackports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package libdvdcss2 has no installation candidate


I'd like some help please

---

### Post by Sutekh on 2006-03-14
Have a read of this link

[Ubuntu Wiki - Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats")

You actually need to install libdvdread3, then run a script to install libdvdcss2, but that's all covered in the Wiki link.

---

### Post by jrib on 2006-03-14
make sure you run 'sudo apt-get update' after editing sources.list too

---

### Post by terranz on 2006-03-14
Thanks for the link.  I'll give a go and post the result.

I did an update and it didn't help.

---

### Post by deathbyswiftwind on 2006-03-14
dude use automatix to install your codecs ;) [http://www.ubuntuforums.org/showthread.php?t=138405&highlight=howto+automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=howto+automatix)

---

