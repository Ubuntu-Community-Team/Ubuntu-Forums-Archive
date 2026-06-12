---
title: "Transmission small issue"
date: 2009-04-16
forum: General Help
---

### Post by Subway on 2009-04-16
Hi there :) i decided to change from windows to ubuntu and so far is quite nice. im trying to figure out a few things but first thing im trying to fix is the torrent client transmission, when downloading a torrent i cant get it to open the torrent to pick-n-choose inside the torrent what i want to download. it will just download the whole torrent by default :( is there a way around this ? thank you for any help.

---

### Post by lovinglinux on 2009-04-16
I don't know if transmission is capable of doing this (probably is), but I would recommend Deluge, which is the best torrent client for Linux and Windows in my opinion.

You need to configure Deluge to use full allocation to be able to select files within a multiple file torrent. When you add the torrent, Deluge will prompt for file selection.

You can get the latest Deluge version from [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

Support and additional info [http://dev.deluge-torrent.org/](http://dev.deluge-torrent.org/)

---

### Post by sisco311 on 2009-04-16
What version are you using? When I add a new torrent I can untick the files in the *Download* tab of the *Add torrent* window or in Properties --> Files. I'm using Transmission 1.51.

To update to the latest (stable) version you have to add the [ppa repository]("https://launchpad.net/~transmissionbt/+archive/ppa").

Instructions here: [https://help.launchpad.net/Packaging/PPA#Adding the keys using Gnome]("https://help.launchpad.net/Packaging/PPA#Adding the keys using Gnome")

---

### Post by Subway on 2009-04-16
Hi and thanks for the reply, could i not just install it from synaptic package manager? would this be fine? thanks again.

sisco311 im using version 1.06

---

### Post by sisco311 on 2009-04-16
> **Subway said:**
> Hi and thanks for the reply, could i not just install it from synaptic package manager? would this be fine? thanks again.

sisco311 im using version 1.06

Both Deluge and Trasmission is outdated in the Ubuntu repositories. After you add the ppa repository you can install the latest version with Synaptic.

deluge repo: [https://launchpad.net/~deluge-team/+archive/ppa ]("https://launchpad.net/~deluge-team/+archive/ppa")

the link to the transmission repository (+instructions) is in my first post.

here is youtube video: [http://www.youtube.com/watch?v=UUZOQsNo_ws]("http://www.youtube.com/watch?v=UUZOQsNo_ws")

---

### Post by Subway on 2009-04-16
Trying now

---

### Post by Subway on 2009-04-16
Ok so i tried to install transmission again with the following error,

transmission-gtk:
  Depends: libdbus-glib-1-2 (>=0.78) but 0.74-2 is to be installed
  Depends: libgtk2.0-0 (>=2.16.0) but 2.12.9-3ubuntu5 is to be installed

i installed this libdbus thing but i get the error still, any idea why? thanks again.

---

### Post by Subway on 2009-04-16
In terminal i get this msg,

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transmission: Depends: transmission-gtk (>= 1.52-0ubuntu0~jaunty1) but it is not going to be installed
E: Broken packages

---

### Post by sisco311 on 2009-04-16
> **Subway said:**
> In terminal i get this msg,

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transmission: Depends: transmission-gtk (>= 1.52-0ubuntu0~jaunty1) but it is not going to be installed
E: Broken packages

Remove the new repository from Software Sources and add
```
deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu hardy main
```if you are using Ubuntu Hardy Heron(8.04)
or
```
deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu intrepid main
```if you are using Ubuntu Intrepid Ibex(8.10)

EDIT:
By default, the repo listed is for Jaunty, it's a drop down list on the ppa page where you can select Hardy or Intrepid ;)

---

### Post by Subway on 2009-04-16
transmission-gtk:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed

transmission-dbg:
 Depends: transmission-gtk but it is not going to be installed

---

### Post by Subway on 2009-04-16
EDIT:
By default, the repo listed is for Jaunty, it's a drop down list on the ppa page where you can select Hardy or Intrepid 

Thank you deb-src [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) hardy main did the trick :) now i can use the updated Transmission 1.52.

Thanks again.

---

### Post by sisco311 on 2009-04-16
You're welcome.

---

