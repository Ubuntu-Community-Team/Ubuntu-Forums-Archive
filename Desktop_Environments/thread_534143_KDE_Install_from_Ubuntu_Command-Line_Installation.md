---
title: "KDE Install from Ubuntu Command-Line Installation"
date: 2007-08-24
forum: Desktop Environments
---

### Post by Anlace on 2007-08-24
Greetings All,

I have a thread going titled "Disillusioned with Kubuntu" at [http://ubuntuforums.org/showthread.php?t=530784](http://ubuntuforums.org/showthread.php?t=530784).  I've been waiting for this weekend so that I can do a complete new KDE installation from an Ubuntu Command-Line installation.

If I understand things correctly these are the steps I'll need to take.  I would very much like to get comments from anyone that has done the same.  Please refer to my other post (above) if you are tempted to answer with "install Kubuntu."

1)  Ubuntu Command-Line install from alternative CD

2)  apt-get install xorg

3)  apt-get install xserver-xorg

4)  apt-get install (in the following order:
          aRts
          kdelibs
          kdebase

5)  apt-get install optional packages as needed.

I am comfortable with hand editing the repository list, I prefer to ftp from osuosl.edu as my primary source for files because I get blazing fast download speeds from them.

Will I need to worry about getting and installing Nvidia drivers prior to have a working KDE desktop?  I can install the driver, and then hand edit xorg.conf for my wide-screen monitor, later in the game as long as I have a usable display until then.

Does it look like I missed anything here?  

I appreciate any feedback I may get.  I intend to write a HowTo when I finish this process (if it works that is).

Peace,
Gail

---

### Post by aysiu on 2007-08-24
Go for it.

The worst that could happen is you forget a package. Then, just install it later with the terminal or Adept.

---

### Post by gatewayasteroid on 2007-08-25
> **Anlace said:**
> 
1)  Ubuntu Command-Line install from alternative CD


ok

> 
2)  apt-get install xorg


ok

> 
3)  apt-get install xserver-xorg


this is not needed

> 
4)  apt-get install (in the following order:
          aRts
          kdelibs
          kdebase


just install kdebase, or kde-core for a little bit more

> 
5)  apt-get install optional packages as needed.


for example kdm

> 
I appreciate any feedback I may get.  I intend to write a HowTo when I finish this process (if it works that is).


it already exists:

[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

:)

---

### Post by Sanne on 2007-08-25
There's also a blog post by Jucato detailing the steps of [installing a minimal Kubuntu Edgy system]("http://jucato.org/kde/kde-core.html").

I haven't tried it myself but plan to do it for my next install. Good luck to you. :)

---

### Post by Anlace on 2007-08-25
Good Morning,

gatewayasteroid you commented to

4) apt-get install (in the following order):
aRts
kdelibs
kdebase
> just install kdebase, or kde-core for a little bit more

This info is in the KDE Installation Guide at [http://docs.kde.org/development/en/kdebase/faq/install.html#id2547444](http://docs.kde.org/development/en/kdebase/faq/install.html#id2547444)
> aRts and then kdelibs should be installed before everything else, and kdeaddons last. The other packages can be installed in any arbitrary order.

Thanks for the links too!

Peace,
Gail

EDIT - After doing a lot of research today I found that kde-core IS arts, kdebase, and kdelibs.  My sincere apologies to you gatewayasteroid!

---

### Post by Sanne on 2007-08-26
Anlace,

in case you haven't found out in your research yet: for info about packages and their contents and dependencies you can go to [packages.ubuntu.com]("http://packages.ubuntu.com/") and browse packages, search for a specific package or search in which package a specific file is in. The single package pages list also their dependencies.

On the command line you can try
> apt-cache showpkg packagename
and you'll get listed the dependencies and also which packages depend on it (Reverse Depends). This method only works if you have the repository of the package in your sources.list so apt knows about the package.

---

### Post by Anlace on 2007-09-09
An update here.

I did a successful install of Ubuntu Command-Line and KDE (without Kubuntu) on my Toshiba Satellite L15 laptop.  Just ran into the usual pain-in-the-butt over wireless but otherwise no surprises.

I really do like the KDE installation outside of Kubuntu.  It's a shame really, I will keep an eye on Kubuntu but will not reinstall it unless there are significant changes.

I know the question has been asked before but why doesn't Ubuntu simply offer the choice of installing either Gnome or KDE as a desktop?  Bare-bones versions of either would be spectacular.  That is if the offered programs aren't stripped down versions (my primary complaint against Kubuntu).

Now, on to getting my desktop computer squared away.

Thanks for all of the input!

Peace,
Gail

---

### Post by gatewayasteroid on 2007-09-10
> **Anlace said:**
> 
EDIT - After doing a lot of research today I found that kde-core IS arts, kdebase, and kdelibs.  My sincere apologies to you gatewayasteroid!

No problem! :)

I can assure you that the kdebase package is enough for a fully functional (while minimal) KDE desktop. I did it so many times (even if I'm using IceWM now) ;)

---

