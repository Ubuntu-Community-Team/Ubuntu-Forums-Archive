---
title: "Install Kubuntu from Hoary 5.04 DVD?"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Rehevkor on 2005-04-11
I was wondering if I can install Kubuntu from the Hoary 5.04 DVD in the same manner I can install it from the Kubuntu CD. I'm asking because the DVD only lets me live boot into Ubuntu with GNOME, which I'm not interested in. Thanks.

---

### Post by clparker on 2005-04-11
wait? there is an ubuntu DVD?

---

### Post by tonym on 2005-04-11
You could just install an Ubuntu system then remove the ubuntu-desktop and gdm packages,  install the kubuntu-desktop and kdm packages and I think you end up with Kubuntu.

---

### Post by Rehevkor on 2005-04-11
That sounds like a crude way to do it, and would most likely cause problems. I would have expected this 3gb DVD to actually let you choose which desktop environment to install, but the installation isn't very interactive at all.

Btw, the DVD iso is on the ubuntu FTP. I think it's cdimage.ubuntu.org or something.

---

### Post by scottlc on 2005-04-11
[QUOTE=Rehevkor]That sounds like a crude way to do it, and would most likely cause problems. I would have expected this 3gb DVD to actually let you choose which desktop environment to install, but the installation isn't very interactive at all.

Btw, the DVD iso is on the ubuntu FTP. I think it's cdimage.ubuntu.org or something.[/QUOTE]
 The correct address for the Hoary DVD releases is:

[http://cdimage.ubuntulinux.org/releases/5.04/release/](http://cdimage.ubuntulinux.org/releases/5.04/release/)

Available for BitTorrent download only. I still haven't found any links to the DVD images on the home page though.

---

### Post by Rehevkor on 2005-04-11
[QUOTE=scottlc]The correct address for the Hoary DVD releases is:

[http://cdimage.ubuntulinux.org/releases/5.04/release/](http://cdimage.ubuntulinux.org/releases/5.04/release/)

Available for BitTorrent download only. I still haven't found any links to the DVD images on the home page though.[/QUOTE]

I know it's on the FTP, because I downloaded it from there myself. Here's the info:

cdimage.ubuntulinux.org, anonymous, port 21
/cdimage/dvd/current/hoary-dvd-i386.iso

The same file can also be reached via /cdimage/kubuntu/dvd/20050407.2
This is what led me to believe that I could install kubuntu from this DVD instead of Ubuntu.

---

### Post by BenediktKratz on 2005-07-15
Hi,

I've noticed that current 'stable' versions (5.04) of Ubuntu and Kubuntu
install/live DVDs are not available by http (or ftp) or are at least not
easy to find. Some mirros have nightly breezy builds of the dvds online
available via http but these do often not work.

To resolve this situation I set up a server on:

[http://nginyang.uvt.nl/](http://nginyang.uvt.nl/)

that hosts the install/live DVD images of Ubuntu 5.04 and Kubuntu 5.04 for
all three platforms (Intel x86, PowerPC and AMD64).

---

