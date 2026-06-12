---
title: "Help installing *.rpm on Fedora"
date: 2009-03-01
forum: General Help
---

### Post by J4m35 M. on 2009-03-01
Hello all~

I'm pretty new to Linux, I can move a little with CLI, not the greatest, but I get the concept.. anyways, Is there a way to install Updates/patches by way of USB drive? I'm in a network competition, and our network doesn't get internet access, so I can't install things through apt-get, or downloading the update. all I get is a 1G Jumpdrive, and one comp with Interweb access.

I need to secure a Fedora core 8 box, which already was hacked, so I had to reinstall.. and Ubuntu 6.06. and i'm lost without apt-get install... so if anyone could help with suggestions on how to install the patches, me <3 you long time.. 

~jim

---

### Post by sgosnell on 2009-03-01
The Fedora equivalent of apt-get is rpm.  I'm not certain of the usage syntax, but it should be relatively similar to apt.

---

### Post by hansdown on 2009-03-01
Hi J4m35 M.

If you were hacked, an update would not fix the problem.

You might consider a fresh install.

[http://lifehacker.com/391067/fedora-9-puts-your-desktop-on-a-usb-drive](http://lifehacker.com/391067/fedora-9-puts-your-desktop-on-a-usb-drive)

---

### Post by J4m35 M. on 2009-03-01
Yeah, I already did a fresh install. need to figure out how to update from a usb so I can reduce chances of being compromised again

---

### Post by hansdown on 2009-03-01
Use the link in my last post.

---

### Post by bodhi.zazen on 2009-03-01
Moved to general help and re-titled , :lolflag:

First, Please use better descriptions of your problem in your titles.

Second, in general, you need to do two things. First re-install, but more important , how were you cracked ? Fix that problem.

Third, we are strongly suggesting you ask questions about other distros on their forums. This is not because we do not want to help, but we feel it is best to help build other distros and help other forums to grow as well. So, since this is a question about Fedora, try the Fedora Forums as well. The people there are helpful and, in general, are going to know Fedora a little better (although there are many here who are familiar with Fedora and many questions are general and apply to any distro).

In general, to install a package, simply mount the usb device, become root, and install.

su #enter root pw and become root

cd /media/your_usb device

rpm -i *.rpm

You probably should connect to the internet and use yum to install as this does not take that much time and otherwise you will need to resolve any dependencies on your own.

---

