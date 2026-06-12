---
title: "KDE and GNOME on Ubuntu?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by lazerradial2003 on 2006-08-16
I'm currently running Ubuntu and while I like the GNOME interface, i'd quite like to have a go with KDE, just so i get an idea about both of them.

I remember in one of my old mandrake installs I could choose which window manager to use and switch between KDE, GNOME and some others (about the only good thing about that mandrake install lol). I was wondering if it's possible to install KDE onto Ubuntu (rather than seperately installiong Kubuntu) and then just choose which one i wanted to use? Thanks.
Edit/Delete Message

---

### Post by ardchoille on 2006-08-16
> **lazerradial2003 said:**
> I'm currently running Ubuntu and while I like the GNOME interface, i'd quite like to have a go with KDE, just so i get an idea about both of them. 

I remember in one of my old mandrake installs I could choose which window manager to use and switch between KDE, GNOME and some others (about the only good thing about that mandrake install lol). I was wondering if it's possible to install KDE onto Ubuntu (rather than seperately installiong Kubuntu) and then just choose which one i wanted to use? Thanks.

Yes, you can install kde on Ubuntu. I installed Ubuntu, and then did:

```

sudo apt-get install kubuntu-desktop

```
Keep in mind that the kubuntu-desktop package is a metapackage and will pull in the kde items for you.

You can switch between gnome and kde by logging out and choosing the other desktop in the gdm screen.

---

### Post by lazerradial2003 on 2006-08-16
Thanks for the quick reply, will try that when i get home, apologies for the duplicate post!

---

### Post by aysiu on 2006-08-16
I would advise using *aptitude* instead of *apt-get*.
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by chadk on 2006-08-16
Couldn't someone just "sudo apt-get remove kubuntu-desktop" ?  Why aptitude?  I've heard this before elsewhere but can't find the reference (and the ubuntu site is dragging REAL slow right now).

---

### Post by ardchoille on 2006-08-16
Hmm.. asyiu has a point.. at least for the time being. apt-get does not uninstall deps when you uninstall a package, aptitude does. The version of apt-get that will ship with Edgy will have support for uninstalling deps because the devs are adding a new option (--auto-remoive if memory serves me), I filed a bug for apt-get about this a while back and a dev emailed me with the new apt-get option info.

---

### Post by aysiu on 2006-08-16
> **chadk said:**
> Couldn't someone just "sudo apt-get remove kubuntu-desktop" ?  Why aptitude?  I've heard this before elsewhere but can't find the reference (and the ubuntu site is dragging REAL slow right now).
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

