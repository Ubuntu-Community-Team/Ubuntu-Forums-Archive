---
title: "How to install KDE on Ubuntu with the help of Kubuntu CD?"
date: 2008-06-29
forum: Desktop Environments
---

### Post by archat68 on 2008-06-29
Hi,
I am new user of Ubuntu hardy 64 bit. I have the Gnome installed. But I want to install KDE on it. I've heard that KDE can be installed on Ubuntu without downloading the packages with the help of Kubuntu Cd.
How to do this?:confused:

---

### Post by aysiu on 2008-06-29
Only if you have the Kubuntu **Alternate CD**. The Desktop CD cannot be used for installed addition to, only an installed replacement for Ubuntu (Gnome).

Once you get a hold of the Alternate CD, paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.nocd
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo mv /etc/apt/sources.list /etc/apt/sources.list.cd
sudo cp /etc/apt/sources.list.nocd /etc/apt/sources.list
```

---

### Post by archat68 on 2008-06-30
I have Kubuntu both alternate disk and desktop disk. 
When I issue the commands, I get:

> arup@arup-desktop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.nocd
[sudo] password for arup:
arup@arup-desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
E: Failed to mount the cdrom.
Why does mounting fails?
But I'm getting the nautilus window when i insert the CD and can browse all the files on it.

So, what to do?
Pls help.

---

