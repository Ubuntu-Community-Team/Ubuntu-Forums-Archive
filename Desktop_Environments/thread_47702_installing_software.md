---
title: "installing software"
date: 2005-07-09
forum: Desktop Environments
---

### Post by ma_deity on 2005-07-09
I like to consider myself fairly computer literate, but I am definatly a linux/unix newbie so now I guess I know how my mother feels when she tries to use Windows....I have a few questions, and was wondering if anybody had some insight.

I was able to succesfully install Kubuntu without trouble,  and I then downloaded several programs from the internet, both .tar.gz files and .rpm files.  How do I go about installing these?  I feel like I am missing something really stupid, because installing downloaded software from the internet should be simple....I was also curiuos if it was possible to install KDE, Gnome, XFCE, or other desktop enviroments and switch between them easily, and if that would slow my computer down.  I have an excessive amount of hard drive space so that isn't an issue, just the speed of the machine when i am running my chosen desktop.

I have 2 windows computers in my house hooked to a router/switch and a little "print server box"...the print server has an ethernet connection that plugs into the switch, and a USB port that goes to my printer.  I have been racking my brain trying to configure linux to work with it.  the manufacturer says it works, but the book mentions nothing about it and they told me to "consult my operating system vendor for information of TCP/IP printing"....Now idea what to do next.

My third and final question for the day is how would I select where my USB thumb dirve gets automatically mounted with a hot plug?  I really want to make it /ThumbDrive or something equally obvious instead of SDA1 or something.

Any help would be greatly appreciated.

---

### Post by pipodnmy on 2005-07-09
1. each distro has its own package format (in general) - ubuntu (being a debian derivative) uses .deb packages. these will be easiest to install.
just do: dpkg -i pkg_name.deb
however, in general you need a repository, which will be listed in /etc/apt/sources.conf (or something similar) and then all you need to do is:
apt-get update //to pick up the new packages from the reps
apt-get install pkg_name //to install new package

in general you can try deb files form diff distros, but prob debian testing will work just as fine and they have a good selection..

---

### Post by pipodnmy on 2005-07-09
2. to switch between window managers, you need a login program..
there are plenty around, some of the most fancy and popular are gdm (if you are using mostly gnome), kdm (if mostly kde), xdm (if you dont care) , etc..
they all have a config section that you list all the window managers that you would like to use, themes, etc..
basicly add one of them to start at start-up and you will see what i mean..
3. for printing look at the KDE print manager (if you use KDE)..
in general, you look up CUPS (common unix printing system - it has a very easy web configuration menu)..
4.that is quite trivial..
in general the device is /dev/sda1 but it gets mounted to /mnt/some_disk_name
this is sort of a convention to mount stuff in /mnt/
However, you can just do:
ln -s /mnt/some_disk_name /ThumbDrive
and this should be exactly what you want..

---

