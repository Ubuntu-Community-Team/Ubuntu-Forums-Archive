---
title: "Terrible thrashing on old machine"
date: 2007-05-23
forum: Desktop Environments
---

### Post by Taejo on 2007-05-23
I've just installed Ubuntu Feisty on a Celeron 1.7 GHz, with 109MB RAM and 390 MB swap (which seemed a bit high to me, but it's what the installer recommended).

I'd been told it would run OK on such a system, but there's a bit of thrashing when I open programs, and I just had at least half an hour of thrashing. I was running the same programs and more just fine with a Mandrake 9.2 install (yes, that's from before it was renamed Mandriva), but I prefer Ubuntu and my mom wanted OpenOffice 2.2.

I've tried Xubuntu, but it isn't much better. Which leads me to believe my machine can cope, but something's set up wrong.

Does anybody have tips on improving performance on systems like this?

Note: I'm not a complete noob --- my own higher-end system has been running Ubuntu for a year --- but I'm having trouble with my parents' box.

---

### Post by techdude2007 on 2007-05-24
Do you have enough RAM installed on the computer?  Ubuntu requires 256 MB Ram and 2 GB of Hard Drive Space.  Do you have these specs on your machine?  Did you put Ubuntu on a second partion of the HDD or does Ubuntu take up the whole HDD?

---

### Post by RedSquirrel on 2007-05-24
Unless you upgrade the RAM, I suggest a barebones install for that machine.

You could setup your own lightweight version of Ubuntu by installing the server edition and then adding Fluxbox on top of that. Once you've done that, you can continue to add apps to your system as you need them, rather than having a whole bunch of apps installed that you may never use.

You can do this with the following guide, which uses the net installer:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

or you could download the server edition CD from [www.ubuntu.com]("http://www.ubuntu.com") and install that and then just do:

```
sudo nano -wB /etc/apt/sources.list
```Comment out (put a # in front of) lines with **cdrom: **in them, otherwise you'll be asked to insert the CD each time you want to install something.

Then

```
sudo apt-get update
``````
 sudo apt-get install xorg xterm gdm fluxbox firefox gksu synaptic

```Configure the X server:
```
 sudo dpkg-reconfigure xserver-xorg
```Start X so you can login to Fluxbox:
```
 sudo /etc/init.d/gdm start
```This will be a very lightweight system. I think you'll be impressed by how fast and responsive it is. :)


[I copied this from a post I made last week. I didn't feel like typing it again, and my other post had some stuff in it that wasn't relevant to your situation. ;)]

---

