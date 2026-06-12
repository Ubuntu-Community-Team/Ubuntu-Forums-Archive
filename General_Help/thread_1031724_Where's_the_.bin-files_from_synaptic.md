---
title: "Where's the .bin-files from synaptic??"
date: 2009-01-05
forum: General Help
---

### Post by Truckerpunk on 2009-01-05
I have a problem with java... LOng story won't come into taht here. But I've trtied to purge it from my hard drive to make a completely fresh java install, but even though I used the purge command in the terminal to get rid of it, when I mark it for installation in Synaptic it says that 3 packages needs to be installed, but NO packages need to be downloaded.So the purge command clearly doesn't work. I wan't to delete them manually then instead but I can't seem to find the place that Synaptic uses to hide the files it stores on my hard disk... Anyone know where this secret place might be?

---

### Post by Nxion on 2009-01-05
How did you install java in the first place?

---

### Post by Titan8990 on 2009-01-05
You can do:

sudo aptitude clean

or

you can check in:

/var/cache/apt/archives

Although, I doubt redownloading the installation file is going to solve any issues.

---

### Post by dcstar on 2009-01-05
> **Truckerpunk said:**
> I have a problem with java... LOng story won't come into taht here. But I've trtied to purge it from my hard drive to make a completely fresh java install, but even though I used the purge command in the terminal to get rid of it, when I mark it for installation in Synaptic it says that 3 packages needs to be installed, but NO packages need to be downloaded.So the purge command clearly doesn't work.
.........

Removing a particular package will NOT necessarily remove any dependencies, since an unknown quantity of other packages may also use those other packages.

The "purge command" does work.

---

### Post by Truckerpunk on 2009-01-06
> **Nxion said:**
> How did you install java in the first place?

It was installed from fresh install of Ubuntu 8.10, but something got messed up and I'm trying to get it to work again. I've tried everythingelse and this is the last thing I can think of. Or else I'm going to have to reinstall Ubuntu again.
Thanks for the answers... Hope I can fix it.

---

### Post by Nxion on 2009-01-06
Do you have the medibuntu repo enabled?

if so, try this:

```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```If you do not have that repo here is how to add it.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```Then:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```After that is done try to insttall java from the first command on this post.

---

