---
title: "removing gnome 3 properly"
date: 2013-03-30
forum: Desktop Environments
---

### Post by Slixt on 2013-03-30
Okay, hopefully I've placed this in the proper place. I recently downloaded ubuntu and I honestly haven't really used Ubuntu since Breezy Badger so, when I was greeted with Unity I was just more confused than anything and decided to try different desktops. I used apt-get to install the latest gnome desktop but, it's even worse than Unity was for me. I'll probably stick with Unity/KDE but, the problem I'm finding now is removing Gnome. I tried taking it out via ubuntu software center. I uninstalled gnome desktop environment and gnome fallback. That however broke my login and aside from looking very wrong compared to what it was, it wouldn't let me log in. I'd click my name and type my password and it'd tell me i'm already logged in. Any ideas on how to get this out of my system before I give up and do a fresh install?

---

### Post by 3rdalbum on 2013-03-31
Welcome back. Seven years is an eternity in Linux and while I'm sure you will like Unity, it is very different to anything you have used before.

Reboot your system and press Control-Alt-F1 to get to a text terminal. Log in there and type the following:

sudo apt-get install ubuntu-desktop
sudo apt-get install --reinstall lightdm

The first line should reinstall any packages that you may have removed that Unity and Gnome both depend on. The second line ensures you have the original display manager and allows you to set it as default again.

---

### Post by pietrucha23 on 2013-03-31
Unity and Gnome 3 share some libs, so you can't remove Gnome 3 totally. There is this page:
[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu) (and links on the left)
saying how to swap graphical environments around on *ubuntu. Won't tell you what exactly to do, but might give you some clues. Last time I used it was on 10.04 LTS and it worked then. To be honest, fresh install seems the fastest solution unless you have a lot of extra software installed you want to keep.

---

### Post by Slixt on 2013-03-31
Okay, thanks. It was a fresh install that I was just beginning to setup. I opted for the easy out and did a fresh install over it. I'll keep in mind how to do this if I get messing with stuff I don't like again. I'm starting to get used to Unity. It was a drastic change from what I'm used to but, during my broken system moment, I seemed to miss it. Ha, funny how that works.

---

### Post by Slixt on 2013-03-31
Thanks again for the help and useful information. Marking as solved.

---

