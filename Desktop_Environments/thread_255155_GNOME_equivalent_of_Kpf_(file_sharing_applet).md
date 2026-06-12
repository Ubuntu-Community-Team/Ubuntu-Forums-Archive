---
title: "GNOME equivalent of Kpf (file sharing applet) ?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by abelthorne on 2006-09-11
Hello,
While trying KDE I found out there is a toolbar applet that is quite useful : Kpf is a mini web server that publicly shares a given directory on port 8081. It's configured in just a few click and seems to be a great solution for sharing files with friends when needed, rather than having to setup a private FTP or Web server or relying on the file transfer capabilities of instant messengers.

Is there an equivalent for GNOME, either as an applet or as independant software ?

---

### Post by ssam on 2006-10-30
try gshare. its in the edgy universe.

to set it up go to **system->preference->file sharing**

to see the shares from another ubuntu machine go to **places -> network servers**.

you will need [zeroconf/avahi]("https://help.ubuntu.com/community/HowToZeroconf") set up.

---

### Post by abelthorne on 2006-10-30
I've installed Gshare and activated Zeroconf.
A "Shared files" folder has been created in my home.

How does someone access the files I put in there from a browser ?

---

### Post by ssam on 2006-10-31
the other machine need zeroconf setup too. then it can see it in nautilus in networks.

for windows machines you need to install [Bonjour for Windows]("http://www.apple.com/support/downloads/bonjourforwindows103.html").

there is more info on the [gshare website]("http://yimports.com/~cpinto/projects/gnome/gshare/").

---

