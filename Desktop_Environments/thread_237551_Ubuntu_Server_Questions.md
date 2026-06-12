---
title: "Ubuntu Server Questions"
date: 2006-08-16
forum: Desktop Environments
---

### Post by adam1v on 2006-08-16
Hi all.. i have a couple of questions if people dont mind helping me out.

I was looking at using Ubuntu as a central storage server application.
We currently have 25-30 people on the network and we are using 3 snap servers which is starting to get slow.

I was looking at setting up web folders (mapped drives?) to replace the snap servers.

I was wondering how easy it might be to setup folder security, so that certain people have only certain rights to these folders (none/read/write etc)?

Also, is the Ubuntu Server edition graphical? from what ive read in different places, it only appears to be command prompt style server?

Having never used linux before ever (although i have preloaded ubuntu live a year or two ago) i am an extreme newbie.

any help is greatly appreciated.

Adam

---

### Post by adam1v on 2006-08-16
apologies for not searching the forum first.. having read another post and the command for the graphical interface.. whats the difference between ubuntu/kubuntu/xubuntu

---

### Post by Bagnaj97 on 2006-08-16
Ubuntu/Kubuntu/Xubuntu just have different user interfaces. Whichever you use is a matter of personal choice, although Xubuntu is the most lightweight and therefore more suited to older hardware. Ubuntu uses the Gnome desktop, Kubuntu uses KDE and Xubuntu uses XFCE. The server version is exactly the same as all of those, just without the graphical interface installed.

---

### Post by adam1v on 2006-08-16
thanks.. any personal recommendations?

I was just about to download Kubuntu.. looks simple.

i know the install command is 
> sudo apt-get install kubuntu-desktop

I assume then i simply download the desktop version of kubuntu and use the command line above for installing the GUI of kubuntu as a simple 'add on' ?

Thanks for the quick reply btw.

---

### Post by Bagnaj97 on 2006-08-16
If you already have ubuntu server installed then ```
sudo apt-get install (k)(x)ubuntu-desktop
``` will install whichever desktop version you want. It should set everything up for you and you can then just log in. I personally use plain ubuntu-desktop with gnome, I tried KDE and found it to be less polished. If you have the disc space then you can install all 3 desktops and it lets you choose at the login screen, although having that many packages installed could slow your system down.

---

