---
title: "Swap Partition"
date: 2009-01-27
forum: General Help
---

### Post by Valok on 2009-01-27
So I've got Ubuntu 8.04 installed on my computer at the moment, but I want to give linux and KDE a go and see how I like those.  But when going over the partitioning schemes I've run into a few questions.

When installing Arch, do I need to make a new /home and /swap?  Or is it possible for the Arch and Ubuntu to share these (and maybe other?) partitions

I probably will my first time around, but I'm just curious about this as this is my first venture into HD partitioning schemes.

---

### Post by taurus on 2009-01-27
You can use the same swap partition for all Linux distros.  However, it's a good idea to create it own / & /home since sharing /home among distros could bring disaster.

---

### Post by ajgreeny on 2009-01-27
You can certainly use the same swap, but for /home it is not quite so simple.  You could use the same partition, but you will need to make separate usernames, ie for ubuntu have **usernameubuntu**, and for arch **usernamearch** (you choose more appropriate names, obviously) and in the ubuntu one, because it is already there, you should have all your documents and photos etc etc, together with your hidden config folders/files for ubuntu.

In the arch username you should have all your config folders/files for that together with softlinks to your docs and photos etc etc. which are already existing in the ubuntu user.

That way you will keep your configurations for each distro separate and still only have one copy of all of your own files.  You can not sensibly use one username for both, or the configurations will conflict with each other and cause big problems.

---

### Post by mb_webguy on 2009-01-27
> **Valok said:**
> So I've got Ubuntu 8.04 installed on my computer at the moment, but I want to give linux and KDE a go and see how I like those.  But when going over the partitioning schemes I've run into a few questions.

When installing Arch, do I need to make a new /home and /swap?  Or is it possible for the Arch and Ubuntu to share these (and maybe other?) partitions

I probably will my first time around, but I'm just curious about this as this is my first venture into HD partitioning schemes.

You can try KDE without installing a new version of Linux.  Just install either the kubuntu-desktop package or the kde package.  The former will install all of the KDE applications included with Kubuntu, while the latter will only install the KDE desktop environment and core applications.  You can choose which environment you use (Gnome or KDE) when you login by clicking on Options and then choosing the desired session type.

The above is also true of the Xcfe desktop environment.

As for your partitioning questions, you should have no problem sharing a /tmp partition, as the contents of this directory are wiped every reboot.  You definitely don't want to share a /home directory, though if you have a partition for your files, you can put symlinks in your various home directories that point to the same shared locations for documents, videos, pictures, etc.  You also may not want to share the swap partition.  While this wouldn't be a problem in most cases, if you plan on using hibernation, sharing swap can be a bad idea, as the contents of memory are written to swap upon entering hibernation.  I have no idea what problems you might run into if you went into hibernation in one version of Linux, switched to another, and then tried to resume the first.  You aren't actually required to have a swap partition, anyway -- you can use a swap file instead.  This may be a better option for a multi-boot system with several different flavors of Linux installed.

---

