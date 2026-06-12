---
title: "Gnome 2.14 in ubuntu 5.10?"
date: 2006-03-15
forum: Desktop Environments
---

### Post by JohnnyWalker on 2006-03-15
Is it possible to upgrade a ubuntu 5.10 installation to gnome 2.14, without a total reinstallation of ubuntu with the next version of ubuntu from installation CD?

---

### Post by Ramses de Norre on 2006-03-15
I think you will need to compile gnome from source then, but I wouldn't start doing that on such a huge package..

---

### Post by magnusbb on 2006-03-15
Not officially - then you would have to upgrade to Dapper Drake.

But, you can always use GARNOME ([http://www.gnome.org/projects/garnome/](http://www.gnome.org/projects/garnome/)). Here you can compile a GNOME 2.14 environment side-by-side with the Ubuntu-stock 2.12 version. It's worth testing if you have the time... and the knowledge (shouldn't be that difficult, though).

---

### Post by Sef on 2006-03-15
> But, you can always use GARNOME ([http://www.gnome.org/projects/garnome/)](http://www.gnome.org/projects/garnome/))

Note: Link gives 404 error.

---

### Post by engla on 2006-03-15
[QUOTE=JohnnyWalker]Is it possible to upgrade a ubuntu 5.10 installation to gnome 2.14, without a total reinstallation of ubuntu with the next version of ubuntu from installation CD?[/QUOTE]
No, I'm pretty sure that will be impossible. Even though you can build the new gnome yourself on a breezy system, the binaries on the dapper cd are not the same. They are built together with all the latest versions of shared libraries, so they won't be "binary compatible" with the shared libraries on a breezy system.

---

### Post by JohnnyWalker on 2006-03-15
How about upgrading 5.10 to dapper then, will that be [officially] possible with the normal update funktion, or do you have to download and iso and burn a cd?

---

### Post by Ramses de Norre on 2006-03-15
sudo gedit /etc/apt/sources.lst
Change "breezy" to "dapper" everywhere.
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by JohnnyWalker on 2006-03-17
A small typo in your suggestion... This is how is shall be, in case someone else wants to try.

sudo gedit /etc/apt/sources.list
Change "breezy" to "dapper" everywhere.
sudo apt-get update && sudo apt-get dist-upgrade

apt-get is running now, I'll let you know how the upgrade went.

---

### Post by JohnnyWalker on 2006-03-17
The installation  is still running, but I am very dissappointed to see that gstreamer0.8 is installed instead of gstreamer0.10. dapper should have gnome2.14, which is using gstreamer0.10??

Get:620 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse gstreamer0.8-faac 0.8.12- 1 [28.4kB]
Get:621 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse gstreamer0.8-faad 0.8.12- 1 [28.3kB]
Get:622 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe gstreamer0.8-ffmpeg 0.8.7-5 ubuntu1 [2303kB]

---

### Post by Xian on 2006-03-17
[QUOTE=JohnnyWalker]The installation  is still running, but I am very dissappointed to see that gstreamer0.8 is installed instead of gstreamer0.10. dapper should have gnome2.14, which is using gstreamer0.10??[/QUOTE]

Dapper is currenty in _development_ and there are many areas that are not complete or finalized, including the package versioning. What exactly did you expect -- a finished product at this point?? You are just like the rest of us, which is to say testing a build that is heavy on change.

---

### Post by JohnnyWalker on 2006-03-17
I expected a mosly working product, with a few glitches, which I might help to find.

I do expect that it already has Gnome2.14 och  gstreamer0.10, which gnome 2.14 is based on.

Are you saying that it has gstreamer0.10, but the package version numbers are wrong i.e. only the filenames are wrong?

---

### Post by JohnnyWalker on 2006-03-17
After running the above apt-get sequency to end and doing a reboot, the system halts with

PCI: Cannot allocate resource reqion 4 of device 0000:00:07.1
Segmentation fault
ALERT! /dev/sda1 does not exist. Dropping to a shell.

So, it is not adviseble, at least not in a vmware environment.

---

### Post by ashrack on 2006-03-29
just curious, how come I could upgrade BREEZY with the latest KDE just by adding a new repo but with GNOME this is not possible, why??

---

### Post by ashrack on 2006-04-04
[QUOTE=ashrack]just curious, how come I could upgrade BREEZY with the latest KDE just by adding a new repo but with GNOME this is not possible, why??[/QUOTE]
anyone

---

