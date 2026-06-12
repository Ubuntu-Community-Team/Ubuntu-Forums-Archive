---
title: "Broken Synaptic after attempted OpenOffice upgrade"
date: 2009-05-08
forum: General Help
---

### Post by FrogPrince on 2009-05-08
Hi,

This is the first time I've used Ubuntu since Drapper Drake, after which I moved onto Debian and then to Archlinux. I heard some wonderful things about Jaunty and I wanted to see for myself. I have to say I'm very impressed! This is a great distribution! It's sooo fast and easy to use! I'd love to be able to shake Shuttleworth and his developers by the hand for this superb release!
Anyway, onto my problem. I wanted to install OpenOffice 3.1 last night (yes, I know, Ubuntu isn't rolling release, but I've got a couple of files that won't open in 3.0 due to a bug), so I added the following lines in sources.list and updated apt-get:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```The trouble is that now whenever I try running Synaptic, apt gets stuck. I've tried the following:

```
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock

```Then 

```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```At first the problem seems cleared, but as soon as I try using apt-get again it starts trying once again to install OpenOffice 3.1 and gets stuck. Is there a way of solving this issue without having to do a complete reinstall?

Thanks for any help.

---

