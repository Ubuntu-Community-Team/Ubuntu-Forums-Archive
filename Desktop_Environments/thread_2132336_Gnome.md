---
title: "Gnome?"
date: 2013-04-04
forum: Desktop Environments
---

### Post by pinballwizard on 2013-04-04
I am sorry if this has been here, and if it has, will a mooooooderation please occur.

I saw on the April desktop thread a guy who had Gnome pretending to be Unity.

Now, I hated Unity and went back to KDE when it was launched, but through a complex series of mishaps, I am so in love with Unity. When I maintain my parents' laptops running KDE, I'm so lost and I end up frastrated cause it's so clunky and agricultural.

So, I'm wondering, between unity and gnome shell, what would I be giving up? I mean could I switch and be as at peace as I am now?

---

### Post by kungfupete on 2013-04-04
> I am so in love with Unity

pinballwizard:  It sounds like Unity is currently meeting all your needs --so what are you missing?  I'm not sure I get where you are going with this.  Is there something preventing you from installing Gnome 3 along side Unity and "kicking the tires" so to speak?

---

### Post by Frogs Hair on 2013-04-04
I run both. when the gnome shell is installed on your existing Ubuntu installation  it uses the Ubuntu applications. Its not like your adding a bunch of extra applications as with Xubuntu and the others. It never hurts to become familiar with another desktop and sudo apt-get remove is quick and effective :P .

---

### Post by markbl on 2013-04-04
Just "apt-get install gnome-shell" and then you can select GNOME at the login window to try it out. It won't affect Unity (called Ubuntu on the login screen selection). You can log in and out of either environment at will to try each out. Both Unity and Gnome Shell are excellent and much better than the older/classic style desktops IMHO.

---

### Post by pinballwizard on 2013-04-05
> **kungfupete said:**
> pinballwizard:  It sounds like Unity is currently meeting all your needs --so what are you missing?

This just looks so good:
> **VinDSL said:**
> Turn Gnome-Shell into a Unity Wannabe.  LoL!  :grin:

* Gnome-Shell 3.8.0.1 / Ubuntu 13.04
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-apr-2013-1%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-apr-2013-1.png")[/INDENT]

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-apr-2013-2%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-apr-2013-2.png")[/INDENT]


I want that.

---

### Post by Frogs Hair on 2013-04-05
Both 13.04 and Gnome 3.8 are for testing at the moment . You can experiment if you have room on your hardrive .Make backups if you plan to use 13.04 as your daily operating systen . 13.04  runs fine for me on my desktop, but the Gnome 3.8 trial was a bt rough so I am back on 3.6 which will ship with 13.04. Many extensions need to be update for 3.8 also.

---

### Post by kinggo on 2013-04-05
> **pinballwizard said:**
> This just looks so good:


I want that.
dash-to-dock extension on the left with intellihide turned on and conky on the right

---

### Post by TeamRocket1233c on 2013-04-05
I like GNOME Shell and Unity both, but adore Cinnamon and really dig MATE.

---

### Post by Allavona on 2013-04-05
I am able to do so much with Gnome. Both Unity and Gnome caught hell at first, but both have come a long way and continue to improve.

---

### Post by pinballwizard on 2013-04-08
Right, Gnome installed, and I'm loving it. I really enjoy the extensions aspect.

---

### Post by pinballwizard on 2013-04-08
Question, using Gnome, can I change the position of the login box?

---

### Post by pinballwizard on 2013-04-17
.

---

### Post by Cheesemill on 2013-04-17
The login screen isn't handled by Gnome, it's all handled by which ever DM (display manager) you are using.

A standard Ubuntu installation will be using LightDM, Kubuntu uses KDM, Gnome Remix uses GDM. However you can have more than one DM installed on a machine, and you probably will do if you have added different desktop environments to your system.

Probably the easiest way to see which DM you are using is to open a terminal and do...
```
ps ax | grep dm
```
and see which processes are running with dm in their name.

Once you know which DM you are running then searching for 'lightdm customization' for example should get you all of the info you need.
Some DM's are highly customizable, others not so much so if your current DM doesn&#8217;t suit your needs you can always install a different one.

If you have more than one DM installed, then you can decide which one should be used when you boot your machine by doing...
```
sudo dkpg-reconfigure lightdm
```
You can use the name of any of your installed DM's in this command, you get the same menu whichever name you use.

For a list of the most common DM's take a look here...
[https://wiki.archlinux.org/index.php/DM#List_of_display_managers](https://wiki.archlinux.org/index.php/DM#List_of_display_managers)

---

