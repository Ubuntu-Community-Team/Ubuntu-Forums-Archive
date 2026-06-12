---
title: "Question on installing xfce desktop"
date: 2011-10-13
forum: Desktop Environments
---

### Post by DFretz on 2011-10-13
I am new to Ubuntu. I want to try Xfce and have read in this forum that you can install as many desktop environments as you like and switch between them. In the Synaptic Package Manager, when I mark the package "xubuntu-desktop" for installation, it tells me that it will UNinstall package "ubuntu-desktop", which doesn't sound like such a good idea. What am I doing wrong if I want both?

---

### Post by thatguruguy on 2011-10-13
You don't need to install the xubuntu-desktop, which will replace your current desktop.  Just look for the xfce4 package and install it.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-13
that is ok....  you want xubuntu-desktop instead of ubuntu-desktop.
However you can just install the Xfce, and switch to that window manager in youre Login screeen


install xfce just run

sudo apt-get install xfce4

That will be different than Xubuntu, but you will have the full Xfce desktop environment.
I hope that helps

---

### Post by westie457 on 2011-10-13
Hi to answer your question "What am I doing wrong?" absolutely nothing. They are both 'Meta' packages (which is to say like a box) that holds all the necessary packages to be installed. They can be removed without losing anything.

---

### Post by DFretz on 2011-10-13
Thank you everyone for your replies. I didn't realize that xubuntu-desktop and xfce were actually different installs. If I just install xfce, does that mean it runs slower than if I install the xubuntu-desktop, because it is running on top of the Unity desktop? I'm just trying to get something that I hope will be more responsive than the Unity desktop that came by default with Ubuntu 11.04, without having to reinstall the existing apps that I use. Thanks!

---

### Post by 3Miro on 2011-10-13
If anything, xfce4 will be faster than Xubuntu.

xfce4 does not run on top or below Unity. When xfce4 is running, Unity, Compiz and Gnome are not running.

The difference between xfce4 and xubuntu-desktop is in the additional bells and whistles installed. xfce4 is the minimum, while xubuntu-desktop will come with lots of extra applets and settings. I am not sure about the exact setup, but my guess would be that xubuntu-desktop will likely load additional things from Gnome 2.

Unless you want to remove Unity and Gnome 2, you should be fine to just install xfce4 and give it a try.

---

### Post by meatytaco on 2011-10-13
Just wanna throw my input in :P. I'm running xubuntu with xfce, oppose to the ubuntu desktop I tried first, xfce is definitely faster on my comp. I was running the lxde, desktop which I believe is just a bit lighter than xfce, but I didn't notice a difference in performance between the two and I personally like xfce better. :)

---

### Post by rojaasensei on 2011-10-13
> **meatytaco said:**
> Just wanna throw my input in :P. I'm running xubuntu with xfce, oppose to the ubuntu desktop I tried first, xfce is definitely faster on my comp. I was running the lxde, desktop which I believe is just a bit lighter than xfce, but I didn't notice a difference in performance between the two and I personally like xfce better. :)

+1 for meatytaco.  I have had the same experience.

With 11.04  I followed the instructions at [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) to convert from unity/gnome to xubuntu

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-22
I had the same experience with lxde....   xfce seems to run faster than lxde.... 4  me

@DFretz
once you install xfce4, all you need to do is log out of your current session, and switch it to xfce4 INSTEAD of Ubuntu.
then login and you will be using xfce.

xfce is different than XUbuntu, there are a lot of different gnome 2 things in play.... but it does use a lot of the "normal" xfce stuff.

---

### Post by TBeholder on 2011-10-22
As to myself, installed the whole thing from Xubuntu startup disk, after having the system wrecked via upgrade to That Thing. Seems fast enough.
But IMHO, install xfce4 and what you really need, *then* see how much of the other stuff would be added with xubuntu-desktop and check whether you may need it.
The two most handy features, anyway, seems to be xfce4-panel itself (launchers can work like drawers) and xfce4-genmon-plugin (Generic Monitor, rocks with grep). See also [on "Xfce Goodies"](http://goodies.xfce.org/projects/panel-plugins/start).

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
oh and Nautilus causes issues with xfce... it will take over your desktop, so if you run nautilus you'll need dconf-tools to change your background image.... nautilus seems to do a little more than thunar, though thunar has mass rename capabilities (i like pyrenamer better) nautilus works with dropbox, and seems to mount things more accurately on my comp.

---

