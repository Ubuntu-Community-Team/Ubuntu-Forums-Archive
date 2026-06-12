---
title: "install another desktop environment for testing"
date: 2014-01-22
forum: Desktop Environments
---

### Post by rxlord on 2014-01-22
hey i have been using unity for quite a while now and now i want to test some other desktop environments so i installed gnome shell but the unity style windows remained and also the login screen didnt changed to gnome.same is the issue with kde lxde etc. plz help i wanna run other DE's alongside unity.

---

### Post by vasa1 on 2014-01-22
Although many people feel it's okay to have several desktop environments together, I've seen quite a few reports indicating that complications occur.

Why don't you install something like VirtualBox and try out different distros in that? To my mind, that's a cleaner approach.

---

### Post by grahammechanical on 2014-01-22
My advice is to create another partition - 20GB - 25GB and, either, install another copy of Ubuntu into that partition  to experiment with or install the full distribution of Xubuntu, Kubuntu, etc., in to it to get the full experience of the flavour. That will avoid completely messing up your working install of Ubuntu, which will require a re-install.

I have tested installing all the desktops of the Ubuntu flavours on one installation. There are most definitely conflicts especially with login screen backgrounds. And each alternative desktop installs much more that a user interface. It brings in all kinds of utilities and applications. I have never installed an alternative desktop from another distribution of Linux but I would expect conflicts. A distribution may claim to be based upon Ubuntu but what version of Ubuntu? The latest? Libraries in Ubuntu are being upgraded from version to version.

Ubuntu uses the LightDM display manager and we get the background image that LightDM is designed to provide. Gnome 3 shell is needs to use the Gnome Display Manager (gdm) if it is to provide the Gnome login screen and background image. If we install Gnome 3 shell on Ubuntu we still use LighDM. I think that you will find that Xubuntu, Kubuntu and Lubuntu also use LightDM although I have noticed that there is a change in background image when those desktops are installed but do not expect the background image to change each time we select a different desktop session. That does not happen.

Regards.

---

### Post by Bucky Ball on 2014-01-22
If you have those desktop environments installed you need to choose 'Sessions' at the login screen. You will see the full selection of available desktop environments. Choose one. Login.

A tip: DON'T install *buntu-desktop if you want to try out just a desktop environment. For instance, xfce4 rather than xubuntu-desktop is what you want if you just want to try the desktop. If you're just trying DEs, then installing lxde, xfce4, gnome and whatever is fine, but still drags in things you don't necessarily want or need. If you are wanting a fuller experience of the various flavours (without 'hybrid' blends), then the suggestions mentioned so far are better; virtual machines or create two or three partitions for your 'playthings'. ;)

Be aware, some hybrids (blends of various desktops and desktop environments) can turn suit your needs perfectly. I had a desktop set up like that for years which I've only just wiped and upgraded, and I always use artwork (and some apps) from the other flavours (e.g. edubuntu-artwork is one of my favourites). I go the minimal install and use pcmanfm and lxterminal with xfce4 desktop with edubuntu-desktop icons, for instance. ;

---

### Post by rxlord on 2014-01-22
plz give me a command which will install gnome so that icons and windows also change to gnome and also the login screen

---

### Post by deadflowr on 2014-01-22
> **rxlord said:**
> plz give me a command which will install gnome so that icons and windows also change to gnome and also the login screen

You already have most of gnome.
Ubuntu is gnome-based system.
I'm guessing what you want is one of the various gnome interfaces.
You have either gnome-shell.
or the fallback/classic style gnome.
You could simply install gnome-shell with
```
sudo apt-get install gnome-shell
```
 or the classic-style with either
```
sudo apt-get install gnome-flashback-session
```
or
```
sudo apt-get install gnome-panel
```
If you want all the gnome interfaces, a quick way to get them is by installing gnome tweak tool
```
sudo apt-get install gnome-tweak-tool
```
If you want to change the login, then install gdm.
(or another display manager)
To change the login run
```
sudo dpkg-reconfigure lightdm
```
then choose the gdm, or other option and that'll be the choice after a reboot.

---

### Post by Bucky Ball on 2014-01-23
Did you follow the instructions in post #4? If you already have gnome installed, it is just a matter of choosing it from Sessions at the login window and logging in ...

---

### Post by rxlord on 2014-01-24
maybe i didnt explain myself properly or the readers didnt understand the question but i solved the problem.
what is said was that when i installed gnome unity theme was mixed into it(the files manager was in unity theme and the other elements were in gnome theme) 
i changed the windows manager to gnome by going to system settings appearence and selecting adwaita.
thank you all for the help 
~ rxlord

---

### Post by deadflowr on 2014-01-24
> **rxlord said:**
> maybe i didnt explain myself properly or the readers didnt understand the question but i solved the problem.
what is said was that when i installed gnome unity theme was mixed into it(the files manager was in unity theme and the other elements were in gnome theme) 
i changed the windows manager to gnome by going to system settings appearence and selecting adwaita.
thank you all for the help 
~ rxlord

Your right,:lolflag:

I was going strictly on your thread title.
It left the impression that you needed help installing a desktop environment.

It should have mentioned theme problems with gnome-shell instead.

In which case, I would've suggested simply installing gnome-tweak-tool, and been done.

---

### Post by poltiser2 on 2014-01-24
I have an old HD 80 GB in USB enclosure... formated with2 partitions 13 GB for system and the rest for home. I installed XU64. I wrote GRUB not (!) to MBR of the original desktop system. I placed GRUB in boot loader on external USB HD with XU64. Choosing from BIOS I can switch between external and internal systems - 2 independend MBRs each with different GRUB - all starting any internal system and external drive starting external system as well. It works with any linux/W7 combination... :D It is even not too slow.
Happy experimenting.

---

