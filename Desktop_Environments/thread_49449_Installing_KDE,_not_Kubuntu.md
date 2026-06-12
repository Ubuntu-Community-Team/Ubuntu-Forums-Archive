---
title: "Installing KDE, not Kubuntu"
date: 2005-07-16
forum: Desktop Environments
---

### Post by foxandxss on 2005-07-16
Hi, seeing that the advanced search doesnt work, i will ask:

I would like to install KDE on Ubuntu but I dont want the Kubuntu's KDE, because Kubuntu works very badly for me: it changes from one window to another by itself, among other things.

Then i need to install a KDE from scratch and configure it at will.

Thanks.

---

### Post by WolfJay_83 on 2005-07-16
I'd start by installing KDE in synaptic package manager.  (System > Administration> Synaptic package manager > KDE desktop environment)  (or use sudo apt-get install for those packages)

On the Kubuntu site it says that the download is basicly the same as installing Ubuntu and then adding KDE, I dont know if this will solve your issues.

Good luck

Ps, in Gnome, you can make the mouse select windows by moving over them in (System>Preferences>Windows)  Does KDE have a simmilar option?  That may help you with that one issue.

---

### Post by foxandxss on 2005-07-16
[QUOTE=WolfJay_83]I'd start by installing KDE in synaptic package manager.  (System > Administration> Synaptic package manager > KDE desktop environment)  (or use sudo apt-get install for those packages)

On the Kubuntu site it says that the download is basicly the same as installing Ubuntu and then adding KDE, I dont know if this will solve your issues.

Good luck

Ps, in Gnome, you can make the mouse select windows by moving over them in (System>Preferences>Windows)  Does KDE have a simmilar option?  That may help you with that one issue.[/QUOTE]
 Hi, thanks for the reply.

I can install KDE with "sudo apt-get install Kubuntu-desktop", but this will install kubuntu system, i only need to install "kdebase".

Thanks :)

---

### Post by debian_n00b on 2005-07-16
apt-repo: deb [http://pkg-kde.alioth.debian.org/kde-3.4.0/](http://pkg-kde.alioth.debian.org/kde-3.4.0/) ./

---

