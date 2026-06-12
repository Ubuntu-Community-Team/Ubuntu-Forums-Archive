---
title: "Ubuntu and Ubuntu Classic options on KDM - Remove?"
date: 2011-05-20
forum: Desktop Environments
---

### Post by jemofthewest on 2011-05-20
Hello forum!

I've been playing with Ubuntu on and off for a few years now, and recently installed Kubuntu 11.04 onto a 16gb mushkin flash drive using this guide:

[http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/](http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/)

Anyways, after finishing installing I believe the only things that I have done is installed the programs on the following two guides:

[http://www.howtoforge.com/the-perfect-desktop-kubuntu-11.04](http://www.howtoforge.com/the-perfect-desktop-kubuntu-11.04)
[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal)

as well as install Fluxbox and some eyecandy.  Yet somehow, all of the GNOME options like Ubuntu and Ubuntu classic that come with the default installation now show up on my KDM options, and it is messing with my Fluxbox and transparency backgrounds.  I could learn to fix those minor problems, but I don't get how this happened and plus I'm tight on space.  Any ideas on how this happened or how I can remove it?  I've already tried the following link:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

And all of it came back as not installed so I have no idea how I can have it on my computer... Thanks!

---

### Post by dabl on 2011-05-20
I would start with 

```
sudo apt-get remove --purge gdm
```

That should pull out the Gnome desktop option from your KDM login screen.

Fair warning -- I have never actually done what you are doing.  Watch your messages and don't proceed if it looks like it will do something destructive.

---

### Post by jemofthewest on 2011-05-20
Thanks for the quick reply!  I tried that, and it wasn't installed either... here is the output:  $ sudo apt-get remove --purge gdm [sudo] password for:  Reading package lists... Done Building dependency tree        Reading state information... Done Package gdm is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.

---

### Post by dabl on 2011-05-21
OK, that proves that only KDM is controlling the user login.

To make sure you have all of Kubuntu, you can issue

```
sudo apt-get install --reinstall kubuntu-desktop
```

I don't know fluxbox, but I think it is also a desktop manager, right?  So it would be in "competition" with KDE to be your desktop environment.  It's OK to have both of them installed, but ... you're going to look at both of them every time you log in.  :)

---

### Post by jemofthewest on 2011-05-22
Well, I'm ok with Fluxbox being on there ;-)

Just the Gnome stuff on the menu...

Honestly, at this point it's kinda become an OCD thing that's bothering me because it appears to be not affecting my hard drive.  I also realized that the transparency issues are my laptops inability to handle the desktop effects, it works just find when I plug it into my gaming PC... so I might just try to just remove it off the KDM menu as an option.  I will try the reinstall though!  Thanks!

---

