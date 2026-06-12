---
title: "Hey guys, new here looking for some help :D"
date: 2009-04-24
forum: General Help
---

### Post by Dominating on 2009-04-24
Ok well i have recently installed ubuntu on my main desktop and just getting used to it and configuring stuff.... I have a duel boot setup atm windows 7 for when i wanna game :), anyway thats not to do with my question :P 

The question is i have a HP ze4300 Laptop that is on its last knees xp runs it so slow its not even funny.. all i really wanna use it for is watching movies / shows of my server and watching youtube also browsing web etc...

I'm looking for the best linux distro so far i have tryed slackware / debian / kubuntu and really couldn't get them working nicely also tryed archlinux but wasn't able to get installed for some reason not sure if i had the wrong cd or what.

The laptop has 256mb of ram so i need somthing thats low on resources.

---

### Post by Rocket2DMn on 2009-04-24
Kubuntu was probably a bit heavy for 256MB of RAM.  I would suggest Xubuntu which uses the Xfce window manager, which is lighter than Gnome in regular Ubuntu and much lighter than KDE in Kubuntu.  If you already have some *buntu installed, you can run
```
sudo aptitude install xubuntu-desktop
``` to get Xfce without having to reinstall the whole system.  Then you can select Xfce as your Session at the login screen.  Otherwise get it here - [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Dominating on 2009-04-24
Sweet thanks for the reply and i have used xubuntu 7.10 and meh it still didn't really like the OS :P, i should really get a new lappy but was just wondering if i could bring the old one alive with a better OS.

---

### Post by Rocket2DMn on 2009-04-24
Well, you will need a lightweight distribution to use, and there are some out there.  If you are looking for a *buntu distributions that is lightweight, Xfce is the lightest officially supported.  However, you can also install the [Fluxbox]("https://help.ubuntu.com/community/Fluxbox") window manager which is even more lightweight.

It sounds like you have done a bit of distro hopping which is always fun and enlightening.  Most any distro will support the ability to mount your server's filesystem of NFS or Samba and watch videos, though you may need to install additional "non-free" (as in freedom) codecs.  In Ubuntu you would want the package ubuntu-restricted-extras.  Some distros support these non-free codecs out of the box.
You should also have no problem browsing the web, checking email, writing documents, etc, in most any linux distribution.

---

### Post by Dominating on 2009-04-24
Ok cool, my other question is, is it possible to say install the new ubuntu 9.04 in without a gui then install fluxbox so start of in text mode?

---

### Post by Dominating on 2009-04-24
Hmm might try archlinux + Fluxbox that might work out nice :D

---

### Post by Rocket2DMn on 2009-04-25
I haven't used Fluxbox, but I think it uses some of the same resources that Gnome does (like gdm).  Unless you a short on disk space, I would just do a normal install and then add Fluxbox afterward.  Arch should be able to use Fluxbox as well.

---

### Post by raymondh on 2009-04-25
> **Dominating said:**
> Sweet thanks for the reply and i have used xubuntu 7.10 and meh it still didn't really like the OS :P, i should really get a new lappy but was just wondering if i could bring the old one alive with a better OS.

try puppy

---

### Post by Rocket2DMn on 2009-04-25
> **raymondhenson said:**
> try puppy

Puppy Linux and Damn Small Linux are *extremely* lightweight distros, small enough to install on a 128MB flash drive with room to spare.  But, they are options, though I tend to only recommend them for computers using lower end Pentium 3s and older.  That's just me though.

---

### Post by hansdown on 2009-04-25
Also, simply mepis is excellant.

[http://www.mepis.org/mirrors](http://www.mepis.org/mirrors)

---

### Post by Greg Xix on 2009-04-25
In response to your original question. Knoppix is a cool little version of Linux.

You may want to try Knoppix if you have a spare 1GB USB Flash drive. Use these instructions for version 5.1.1

**[http://www.pendrivelinux.com/usb-knoppix-510/](http://www.pendrivelinux.com/usb-knoppix-510/)**


But for step 2 of that tutorial, get version 6.0.1

**[http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)**

and download from the first Link.

---

### Post by hardyfan on 2009-04-25
The March issue of PC user magazine has UserOS Netbook (a cut down version of Xubuntu for Netbooks).  It runs great on my very old Dell inspiration with 256mb RAM.  I'm sure it is available on there website.

---

### Post by RedSquirrel on 2009-04-25
> **Dominating said:**
> Ok cool, my other question is, is it possible to say install the new ubuntu 9.04 in without a gui then install fluxbox so start of in text mode?

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

After you install the command-line system and reboot without the CD, run:

```
sudo apt-get update
sudo apt-get install xorg fluxbox
startx

```That will get fluxbox up & running. From there, you can open a terminal and install anything else you want.

---

