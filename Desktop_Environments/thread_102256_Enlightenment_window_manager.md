---
title: "Enlightenment window manager"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Akya on 2005-12-11
would some one help me instal enlightenment?

---

### Post by Iandefor on 2005-12-11
what problems are you having? Or are at a loss as to where to look for it?

---

### Post by Akya on 2005-12-11
i actually got it installed but now what do i do as to do anything with it?

---

### Post by Iandefor on 2005-12-11
[quote=Akya]i actually got it installed but now what do i do as to do anything with it?[/quote] The command to run it is: ```
enlightenment
``` To use it on it's own, create a file in /usr/share/xsessions and call it enlightenment.desktop. Put the following in there:

[B][Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application[/B]

Log out, and login using the new session titled Enlightenment.
That's just to use Enlightenment. to get it to work with GNOME, I suggest you use poofyhairguy's [Enlightened GNOME howto]("http://www.ubuntuforums.org/showthread.php?t=54476"), (I feel like I've been referencing that howto far too often lol) and to get it working with XFCE, use my [Enlightened XFCE howto]("http://www.ubuntuforums.org/showthread.php?t=101066").

---

### Post by taurus on 2005-12-11
[QUOTE=Akya]would some one help me instal enlightenment?[/QUOTE]
Didn't I tell you to prepare to spend some time configuring it once you have it install on your system?  When you first use it, it comes with a default setup which may or maybe be what you are looking for.  Therefore, you have to configure it, just like any other window manager...

---

### Post by fossiili on 2008-03-10
I installed OpenGeu wich is an Ubuntu 7.10 derivative with the Enlightment VM. A lot of Gnome-stuff is also included. OpenGeu works well (thank's to Ubuntu) and I also like very much the E17 desktop, although it is still on some kind of beta-stage.

But there is also one problem which I ones met when I had Ubuntu's Gnome-desktop. I have three hard disks and at least seven partitions on them. Each one is represented on the desktop by an ikon, not very stylistic. I can temporary remove them but when I login again, they are there sticking to my eye  #-o

How to remove the "hard-disks" from the desktop?
........................

There is also an other problem but I suppose it is related to Enlightment. On the right side of the desktop stayes a vertical curtain-rod. It ones appeared.  I can not draw the curtain on or do anything for it with the mouse.  :(

Do you know any forum where I could tell about those strange phenomena  in Enlightment? OpenGEU seems not to have any forum.

---

### Post by smartboyathome on 2008-03-11
The only way I have seen to talk to the devs on E17 is to use their IRC channel on freenode (#enlightenment).

Also, you have to edit an option with GConf (cant remember which one, sorry). This will make it so no disk icons show up on the desktop.

---

### Post by bharadwaj on 2008-03-12
does adding enlightment to start up manager deleting nautilus work anything.....and did you search for any key in the gconfeditor?

---

