---
title: "removing kubuntu-desktop"
date: 2007-11-27
forum: Desktop Environments
---

### Post by duncancan on 2007-11-27
Hi everybody,

Firstly, I must say, Ubuntu Studio Gutsy is a *massive* improvement over Feisty..!

Anyway, after dabbling in Fedora core, et al (after cutting my linux teeth on Ubuntu Studio Feisty), and not being happy with them, I installed Ubuntu Studio Gutsy and it's great. The only problem is, I installed kubuntu-desktop (the package), because I've also had -- and enjoyed -- Kubuntu, and it took over the login screen and splash screen of Ubuntu Studio..!

So now, when I turn the computer on, the first thing I see after the BIOS is a Kubuntu loading bar, followed by a Kubuntu login screen...after logging in, if I select Gnome as my session, it looks like normal old Studio again, which is what i want. 

But I want the Studio login screen and splash screen back! I've even decided I'd rather use Studio's Gnome interface, rather than KDE, so I'm happy to remove kubuntu-desktop entirely.

One last thing I should mention; I can't shut down anymore, from Gnome, without first logging out, which returns me to the Kubuntu login screen, from where I can select "shut down".

Unfortunately, "sudo aptitude remove kubuntu-desktop" didn't work. I just want it to work as it did before i ever installed kubuntu-desktop. Any ideas?

Thanks in anticipation,
-Duncan

---

### Post by mrmiserable on 2007-11-27
synaptic package manager

search kubuntu-desktop

right click remove

---

### Post by TeaSwigger on 2007-11-27
Yes. You'll find the full kubuntu package list for your perusal (or removal) at:
[http://www.psychocats.net/](http://www.psychocats.net/)

If you simply want to remove the kubuntu boot splash and login, well that's KDM, as opposed to gnome's GDM. 

Sudo up this file: /etc/X11/default-display-manager

and insert either:
/usr/bin/kdm
or
/usr/sbin/gdm

:)

---

### Post by duncancan on 2007-11-27
hey guys.

thanks for all your help :) my problem is now solved!

mrmiserable, i'd already tried removing kubuntu-desktop, but i think it's a 'virtual' package (?), so it didn't remove any of the packages within it, like amarok, kdm, etc, and only freed 45.7kB of disk space..!

and TeaSwigger, changing /etc/X11/default-display-manager to /usr/sbin/gdm solved half the problem -- i got back the gnome/Studio login screen, but the splash screen was still kubuntu. so thanks for that!

after some googling, for those who are interested, i got the Studio splash screen back by removing kubuntu's usplash artwork: *sudo aptitude remove kubuntu-artwork-usplash*

thanks everybody for your help!
-duncan

---

### Post by TeaSwigger on 2007-11-28
You're welcome :)

Gosh I didn't know you needed to change the usplash too, or I'd have added this... so for any interested, to change the usplash from one to another without uninstalling any:

Run in the terminal:

```
sudo update-alternatives --config usplash-artwork.so
```

It'll show the available options. Choose desired usplash.

Then run in the terminal:

```
sudo dpkg-reconfigure linux-image-$(uname -r) 
```

Glad to see it worked for you, enjoy the ubuntu!

---

