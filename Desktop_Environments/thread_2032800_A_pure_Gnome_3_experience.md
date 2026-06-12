---
title: "A pure Gnome 3 experience?"
date: 2012-07-24
forum: Desktop Environments
---

### Post by dagroves on 2012-07-24
I know the work PURE can be a wee bit vague, but let me explain. I have installed Lubuntu 12.04 on my PC. I wanted to try out Gnome 3, so in a terminal I did ```
sudo apt-get install gnome-shell
``` and I am now using Gnome 3. BUT, is there a way to use Gnome programs and applications and not use the Lubuntu ones? Basically I now want to remove all traces of LXDE and install all of Gnome 3 and its goodies. How do I do that and not break my system?

---

### Post by CaptinGoogle on 2012-07-24
Try sudo apt-get install gnome

The only way I know of removing all the other programs is by removing them one by one. Or in one big command. Perhaps there's a better method.

---

### Post by dagroves on 2012-07-24
> **CaptinGoogle said:**
> Try sudo apt-get install gnome

The only way I know of removing all the other programs is by removing them one by one. Or in one big command. Perhaps there's a better method.

Well I already have Gnome installed, I just want LXDE gone. And I am worried that if I remove it, my system will break.

---

### Post by ajgreeny on 2012-07-24
Try [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by dagroves on 2012-07-24
> **ajgreeny said:**
> Try [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

That worked, but now I have Gnome 3 and Unity... I just want Gnome 3. Is there a way to have Ubuntu with just Gnome 3?

---

### Post by cortman on 2012-07-24
> **dagroves said:**
> That worked, but now I have Gnome 3 and Unity... I just want Gnome 3. Is there a way to have Ubuntu with just Gnome 3?

Start with the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD/") and install GDM and gnome-shell. Or else install Debian Wheezy, which is about as pure a Gnome system as you'll find (uses all the Gnome project's apps).

---

### Post by deadflowr on 2012-07-24
> **dagroves said:**
> That worked, but now I have Gnome 3 and Unity... I just want Gnome 3. Is there a way to have Ubuntu with just Gnome 3?

Yeah, just don't log into unity. gnome and unity run the same apps.

---

### Post by ajgreeny on 2012-07-25
Or just uninstall unity, if you really want, but it takes very little space, so why bother?

---

### Post by Frogs Hair on 2012-07-25
You may want to install Evolution mail and Calendar which is the default calendar that opens from the top panel. You may want the Gnome Desktop Utilities also.

---

### Post by wheeze on 2012-07-25
> **cortman said:**
> Start with the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD/") and install GDM and gnome-shell. Or else install Debian Wheezy, which is about as pure a Gnome system as you'll find (uses all the Gnome project's apps).

This is what I do for almost all my installs. I'm currently running 12.10 on GNOME Shell, no Unity or anything else installed. It's as pure a GNOME 3 setup as you can get in Ubuntuland.

---

