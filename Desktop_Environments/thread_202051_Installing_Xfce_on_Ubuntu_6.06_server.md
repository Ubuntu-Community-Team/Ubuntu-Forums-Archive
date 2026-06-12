---
title: "Installing Xfce on Ubuntu 6.06 server"
date: 2006-06-22
forum: Desktop Environments
---

### Post by nick1 on 2006-06-22
Greetings,

I just installed Ubuntu 6.06 server and I now want a lightweight GUI for it.  I'm thinking Xfce might be a good choice but how do I install Xfce on Ubuntu 6.06 server?

I'm also a little confused about the difference between Xubuntu and Xfce.  I want the Ubuntu 6.06 server system with Xfce on top.  How can I go about making this happen?

Thank you for your time,

*Nick*

---

### Post by MetalMusicAddict on 2006-06-22
I *think* you can do a **sudo apt-get install xubuntu-desktop** to get Xubuntu. Not sure about just XFCE. Im actually gonna use Xubuntu for my next server install but from the Xubuntu CD.

---

### Post by Agent86 on 2006-06-22
[This]("https://help.ubuntu.com/community/InstallingXubuntu") page will tell you how to install Xubuntu-desktop on top of a servier install. I think this is what you want, since Xubuntu is based on XFCE, and this method should avoid installing the Gnome libraries that aren't necessary for XFCE.

If you want to install Gnome stuff later, you can easily do it using apt-get. But you probably want to only install GTK-based software to maintain the "lightness" of XFCE.

---

### Post by ChrisNTR on 2006-06-22
I installed XFCE on Ubuntu Desktop using
sudo apt-get install xfce4

I presume it'd be something similar :)

---

### Post by nick1 on 2006-06-22
Thanks for replying.  ChrisNTR, did you have to enable any repositories?  If so, which ones?

Thanks,

*Nick*

---

### Post by ChrisNTR on 2006-06-23
I've got all the repositories enabled but I think it's in Universe. :)

---

### Post by patrick295767 on 2006-06-23
with a decent /etc/apt/sources.list
  
```
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xorg
apt-get -f -y install xterm
apt-get -f -y install gdm
apt-get -f -y install xcfe4
```
  
Try : apt-get -f -y install fvwm 
this desktop is also very light & customizable

---

### Post by palintheus on 2006-06-23
I know this is a very simple question, maybe I have been staring at the screen to long...I don't know. 

I know the tutorial says to simply type server at the boot screen. I assumed this was by pressing F6 adn erasing everything except 'boot=' and add server. This did not work so I tried just adding server to the end and that did not work.

Please help

---

### Post by nick1 on 2006-06-23
I believe you just type the word server at the initial screen and hit enter.  I don't think you have to edit anything.  Another option is to download the Ubuntu 6.06 server cd and choose the first option when you boot from the disk:  install to hard drive (along those lines).  There's also an option to install a LAMP server, if you have the need to.

*Nick*

---

### Post by palintheus on 2006-06-23
so when the options for Start or Install Ubuntu, Boot from first Hard Disk, etc. just type server and hit enter?

I tried that and it started the live CD......in very lost.....

---

### Post by nick1 on 2006-06-23
I think you first should ask yourself two questions:

1.)  Do I want to run an Ubuntu server?
or
2.)  Do I want to run an Ubuntu workstation?

If you're planning on running services such as Apache, MySQL, PHP, or serving files out to users on the internet, then you want to setup a server.  Download  the Ubuntu 6.06 server cd.

If you want to browse the web, play games, listen to music, etc., then you want to install a workstation.  Download the Ubuntu 6.06 desktop cd.

With the server cd, you can choose to either install to hard disk, which doesn't install services like Apache, MySQL, or PHP.  Or you can choose to install a LAMP server - Linux, Apache, MySQL, PHP.

I haven't tried out the Ubuntu 6.06 desktop yet, so I'm not sure what the install screen looks like.  But imagine you would just want to choose install to hard disk, or similiar option.

The install screen should look similiar to this one:

[http://www.simplifiedcomplexity.com/images/screenshots/dapper/flight3/gfxboot-theme-splash-big.png](http://www.simplifiedcomplexity.com/images/screenshots/dapper/flight3/gfxboot-theme-splash-big.png)

*Nick*

---

### Post by palintheus on 2006-06-23
I want a workstation, but I wanted Xfce, since I have an older system, and I as trying to avoid having both Gnome and Xfce installed.

This is what the screen I get at boot

[http://shots.osdir.com/slideshows/659/1.gif](http://shots.osdir.com/slideshows/659/1.gif)

---

### Post by nick1 on 2006-06-24
This document might be of interest to you:

[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

It was passed along to me when I was interested in installing a server with Xfce.  This would provide a very minimal install with Xfce on top of it.  You can then add whatever applications you want later on.  It sounds like Xubuntu is the Ubuntu version of Xfce: [http://www.xubuntu.org/](http://www.xubuntu.org/)

*Nick*

---

### Post by palintheus on 2006-06-24
This is where I run into the problem of where to type server, and the screenshots that are linked are no longer available. Thanks for all your help, but I think I will just stick with Gnome and Xfce for now...

---

### Post by patrick295767 on 2006-06-24
[QUOTE=palintheus]I want a workstation, but I wanted Xfce, since I have an older system, and I as trying to avoid having both Gnome and Xfce installed.

This is what the screen I get at boot

[http://shots.osdir.com/slideshows/659/1.gif](http://shots.osdir.com/slideshows/659/1.gif)[/QUOTE]
  
download alternate cd iso of dapper, 
make SERVER installation 
then you have installed a dapper with 340 MB only of required packages for dapper 
  the minimum
  
Then you wisely install packages one per one ... 

We Like LINUX !

---

