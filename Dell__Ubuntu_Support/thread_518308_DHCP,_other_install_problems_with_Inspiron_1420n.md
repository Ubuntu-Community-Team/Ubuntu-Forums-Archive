---
title: "DHCP, other install problems with Inspiron 1420n"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by sayhar on 2007-08-05
I'm trying to install kubuntu on my dell 1420n. 

First off, I can't get broadband internet, dhcp fails during the install.

So[ this thread]("http://ubuntuforums.org/showthread.php?t=509408")tells me to download packages and then dpkg them on my 1420n.

I use my windows box to download them, use flash drive to transfer to new "packages" partition. Then I try to dpkg like the guide said.

When I try to do this:
sudo dpkg -i xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb

I get all sorts of errors about needing libc6 or something.

I tried following the advice of [here - ]("http://ubuntuforums.org/showpost.php?p=3117500&postcount=49") and dpkg all of those, but I still get errors.

What am I to do? Thanks in advance.

---

### Post by smithno on 2007-08-06
This is too late, and not going to help, but you don't have to install Kubuntu to get KDE. I assume that you have already blown away Ubuntu, but if you kept the Dell recover partition, you might recover and just install KDE from Synaptic once you get Ubuntu back up and running. That's what I did and I couldn't be happier! All of the drivers from the original Ubuntu still worked and I can swap between Gnome and KDE if I want. I never do, but I can.

---

### Post by sayhar on 2007-08-06
Thanks, but I already wiped the original ubuntu off.

---

