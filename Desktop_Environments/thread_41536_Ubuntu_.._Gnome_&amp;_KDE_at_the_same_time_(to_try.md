---
title: "Ubuntu .. Gnome &amp; KDE at the same time? (to try both)"
date: 2005-06-13
forum: Desktop Environments
---

### Post by dudinatrix on 2005-06-13
I recently installed Ubuntu.. and since I'm a linux n00b, I'd like to give KDE a try.  Of course, being a linux n00b, I also have a ton of questions :)

(1)  Can I have both gnome and KDE installed, and switch between the two on the fly?
(2)  If so, how do I go about installing KDE and leaving my gnome installation in tact?
(3)  Are some applications specific to KDE and some to gnome?
(4)  If so, what happens to the applications that aren't "compatible?"
(5)  Firefox, for example, has gnome-support installed.  Will it work in KDE?
(6)  Will it take any configuration to set up KDE, or is it pretty much up and running after the install?

Ok, 6 questions should cover me for now ;)

---

### Post by SGC on 2005-06-13
> (1)  Can I have both gnome and KDE installed, and switch between the two on the fly?
Yes.

> (2)  If so, how do I go about installing KDE and leaving my gnome installation in tact?
Open the terminal and type the following to install kde:
sudo apt-get install kubuntu-desktop

> (3)  Are some applications specific to KDE and some to gnome?
Yes, but if you have kde and gnome installed they will run on both desktop enviroments no matter which one you are using.

> (5)  Firefox, for example, has gnome-support installed.  Will it work in KDE?
Yes it will works on KDE

> (6)  Will it take any configuration to set up KDE, or is it pretty much up and running after the install?
During the installiton you will be asked if you want to use KDM or GDM, If you don't know what those choose GDM, the one that comes with your ubuntu.


Finally after installing KDE, you will find an option in the login screen where you can choose either KDE or gnome.

---

### Post by dudinatrix on 2005-06-13
*Thank you!*  Sounds good to me... I'm going to try out the Kubuntu LiveCD before installing it, just to give it a little go before-hand.

You pretty much confirmed what I thought it would be like, although I didn't know having both gnome and KDE installed would support both applications in either desktop.. that's awesome!

One more question... :)

(7) Will having both KDE and gnome installed make my system any slower?

---

### Post by ltmon on 2005-06-13
[QUOTE=dudinatrix]*Thank you!*  Sounds good to me... I'm going to try out the Kubuntu LiveCD before installing it, just to give it a little go before-hand.

You pretty much confirmed what I thought it would be like, although I didn't know having both gnome and KDE installed would support both applications in either desktop.. that's awesome!
[/QUOTE]

You can run an application in either environment, but if it's in the environment it wasn't designed for (i.e. firefox in kde) it tends to look pretty ugly and not integrate well with the rest of the desktop.  This annoys some people more than others.

> 
One more question... :)

(7) Will having both KDE and gnome installed make my system any slower?

In general no.

If you are running a kde app inside gnome, then both the gnome and kde libraries are going to be loaded.  This will take up memory, so if you're short this may cause a slow down.  This only happens if you actually run the apps... otherwise it only takes up disk space :)

---

### Post by SGC on 2005-06-13
> 
You can run an application in either environment, but if it's in the environment it wasn't designed for (i.e. firefox in kde) it tends to look pretty ugly and not integrate well with the rest of the desktop. This annoys some people more than others.


To solve this problem use a package that called gtk2-engines-gtk-qt, you can finding it in synaptic, it uses kde's theme and fonts on gnome application so they look nice in kde.

---

### Post by dudinatrix on 2005-06-13
Oh wow.. I just booted the Kubuntu LiveCD and I'm loving KDE.  :) 

Going to install the kubuntu-desktop right now :)

THANKS!

---

### Post by SGC on 2005-06-13
The command will install a similar copy to what you got in the live cd. 

To install koffice you need to enable the universe reposotiry then:
sudo apt-get update
sudo apt-get koffice

---

