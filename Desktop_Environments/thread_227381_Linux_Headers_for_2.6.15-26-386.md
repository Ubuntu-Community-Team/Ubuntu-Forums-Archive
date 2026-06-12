---
title: "Linux Headers for 2.6.15-26-386"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Wilts on 2006-08-01
I am trying to install a older version of ndiswrapper to use my WG511v2 card and am following the instructions here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%2FDriver%29)

However, when I get to the section 4.1, install kernel headers and run the command

  sudo apt-get install linux-headers-$(uname -r)

I get the error 

E: Couldn't find package linux-headers-2.6.15-26-386

I have tried looking for the package at 

[http://packages.ubuntulinux.org/dapper/devel/linux-headers-2.6.15-26](http://packages.ubuntulinux.org/dapper/devel/linux-headers-2.6.15-26)

but the 386 version does not seem to be available.

I suspect that I am being a bit silly but where do I get these headers from?

TIA

Cheers

Paul

(definite Linux newbie)

---

### Post by az on 2006-08-01
You installed using the desktop cd?  It contains a repository with theat package on it.  That repo is apart from the live session.

When at your ubuntu desktop, insert the live cd and wait for a dialogue box to appear asking you if you want to start the package manager.  Say yes and you will be able to install linux-headers-386

---

### Post by Nikku49 on 2006-08-01
im having the same problem, except im trying to install the latest drivers for my graphics card, and i need linux headers for 2.6.17.7

---

### Post by az on 2006-08-01
> **Nikku49 said:**
> im having the same problem, except im trying to install the latest drivers for my graphics card, and i need linux headers for 2.6.17.7

If you have the main repositories enabled, install the linux-headers-386 (or linux-headers-686, -k7 - whatever your CPU) package and that will always depend on th0 emost recent linux-headers-xxxx package.  That works for Edgy as well, in your case.

---

