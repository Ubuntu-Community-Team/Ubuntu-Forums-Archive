---
title: "Downloading Skype and IRC Client"
date: 2009-02-05
forum: General Help
---

### Post by Josshill on 2009-02-05
Alright. I downloaded the Installer for Skype, Ubuntu and everything. When I went to install it. It said "Error: Wrong Architech i386". Also does anyone have a link to a download of a good IRC client for Linux?

Thanks,
Joss

---

### Post by ibutho on 2009-02-05
Hi and welcome to the forum.

For irc clients, you could install xchat (if using gnome or xfce) or konversation (if using kde). These are available in the Ubuntu software repositories, so its a matter of running Synaptic or the Add/Remove software program and selecting the package you wish for installation.

As for skype, download the Ubuntu or Debian version from the skype website and then install it by doing
```
sudo apt-get update
sudo apt-get install gdebi
sudo gdebi skype-{VERSION}.deb
```
The commands basically install gdebi which helps install packages. After that gdebi installs skype for you. Replace skype-version.deb with the actual filename you downloaded from the skype website.

---

### Post by Josshill on 2009-02-05
> **ibutho said:**
> Hi and welcome to the forum.

For irc clients, you could install xchat (if using gnome or xfce) or konversation (if using kde). These are available in the Ubuntu software repositories, so its a matter of running Synaptic or the Add/Remove software program and selecting the package you wish for installation.

As for skype, download the Ubuntu or Debian version from the skype website and then install it by doing
```
sudo apt-get update
sudo apt-get install gdebi
sudo gdebi skype-{VERSION}.deb
```
The commands basically install gdebi which helps install packages. After that gdebi installs skype for you. Replace skype-version.deb with the actual filename you downloaded from the skype website.

How do I get to the area where I enter the code?

---

### Post by hyper_ch on 2009-02-05
add medibuntu repos to get skype on 64bit.

and irc client: xchat, konversation, ....

---

### Post by donkyhotay on 2009-02-05
If you're wanting to install skype using 64bit definitely use the medibuntu repositories. It will save you *a lot* of headaches.

---

### Post by ibutho on 2009-02-05
> **Josshill said:**
> How do I get to the area where I enter the code?

Applications -> Accessories -> Terminal.

---

