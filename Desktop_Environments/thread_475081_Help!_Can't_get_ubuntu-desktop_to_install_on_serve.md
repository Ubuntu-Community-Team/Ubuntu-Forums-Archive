---
title: "Help! Can't get ubuntu-desktop to install on server.  No net connection on machine."
date: 2007-06-15
forum: Desktop Environments
---

### Post by ehull82 on 2007-06-15
Hi Everyone,

I have posted this problem in the Beginner Forum and the Installations & Upgrades forums and have not received any help.

How I do you install additional packages from the Ubuntu CDs in the CLI without an internet connection?

I am running Ubuntu Server 7.04 on my PC and I want to install the Gnome Desktop to try and make learning the OS a bit easier but I don't have an internet connection (in the process of moving). I have the both of the Ubuntu install CDs, server and desktop, but the package won install.

I have tried 
> you should be able to load the ubuntu-desktop packages from your desktop cd.

check your /etc/apt/sources.list to include your installation cd.
you will be looking for a line like this : 
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

sudo apt-get update
sudo apt-get install ubuntu-desktop

that should load the gnome and all depenancies

Which doesn’t work as it says I need to run apt-cdrom add.  I then tried

> with cd in drive.

[code[
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
[/code]

(or you might prefer xubuntu-desktop or kubuntu-desktop)

which does not work.  I finally tried “find –name *ubuntu-desktop*.deb” at the root level with both CDs mounted and it returns that there is no file by that name.  I tried “find –name *ubuntu-*.deb” next and it find the ubuntu-minimal and ubuntu-standard files.

I finally did a search while on a machine at work for ubuntu-desktop .deb package and found [http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop](http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop) 

I downloaded the i386 .deb file, burned it to a CD and even using that CD it won’t install (it says the CD isn’t a debian CD). I've tried everything I can to get apt-get to see that file and it is so beyond frustrating since it just won’t work!
 
Please help!

-Eric

---

### Post by smartboyathome on 2007-06-15
while the cd is mounted:

dpkg -i /path/to/file.deb

That will install the .debs for you. :)

---

