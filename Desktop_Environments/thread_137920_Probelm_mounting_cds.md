---
title: "Probelm mounting cds"
date: 2006-02-28
forum: Desktop Environments
---

### Post by GQed76 on 2006-02-28
I just switched to KDE from Gnome.  In gnome I insert a CD and it mounts, and appears on my desktop.  Now I place the CD in and Konqueror opens and i get an error that it cant mount the cd.

Ideas?

---

### Post by gingermark on 2006-02-28
Konqueror opens due to a program called ivman.

Have a look at [this thread](http://ubuntuforums.org/showthread.php?t=90457) to sort that bit out. (I would recommend using the kdesu command instead of the sudo command when running Kate though).

Hopefully Konqueror is simply trying to read the CD before it's had a chance to mount. I'm not sure why the automount wouldn't be working. It works very well in KDE 3.5.1, so an "idea" (hey, you asked for them :)) could be to upgrade.

To do that, add one of the following mirrors to your sources.list file (located in /etc/apt):
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu) breezy main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu) breezy main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu) breezy main

Then do 'sudo apt-get update' followed by 'sudo apt-get dist-upgrade'.

If you want to verify things, do the following to add the digital key:
```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

If you don't fancy doing that hopefully someone can help you with your version of KDE. If you have the time and the bandwidth I'd recommend upgrading though.

---

### Post by GQed76 on 2006-03-01
Hrrm upgrade didnt work.  Let me see if it works in Gnome

---

### Post by gingermark on 2006-03-01
My apologies, all that stuff works really nicely for me in KDE 3.5.1, I honestly thought that would help.

ivman really should take care of mounting your CDs for you. I appreciate reading back through my previous post I didn't make that explicitly clear. But yes, that's where you should probably focus your efforts.

Once again, sorry if you feel I led you astray.

---

