---
title: "new Desktop enviroment"
date: 2014-04-21
forum: Desktop Environments
---

### Post by windowsfree on 2014-04-21
Hello,

I would like to attempt using a different desktop manager.  I would like to try Gnome, Cinnamon and Mate.  I am currently running Xubuntu 14.04 and I want to test the other desktops impact on performance.  Specs of computer below.  Where do I go to install these desktops? 

[B][URL="http://ubuntucounter.geekosophical.net/img/ubuntu-user2.php?user=29304"][COLOR=#000000]Xubuntu 14.04 (32bit) 
Lenovo Ideapad S10-2
[/COLOR][/URL][COLOR=#000000]2 gig ram
Atom Proc.[/COLOR][/B]

Thank you,

---

### Post by ibjsb4 on 2014-04-21
For gnome-flashback install to 14.04

```
sudo apt-get install gnome-session-flashback
```

Note:  This is not the same as ubuntu-gnome, which runs inside gnome-shell.

---

### Post by windowsfree on 2014-04-21
Thank you for the quick reply,  I take it then this DE is something similar to Mate.  Any ideas on cinnamon?

---

### Post by ibjsb4 on 2014-04-21
I have not ran cinnamon or mate.  Been using my own spin of Flashback (fallback) for a few years on a dual core setup.  I don't know what Atom is capabile of.

Currently I have a old (12 years) box set up with LXDE and trying to get it set up for the real world, gnome is too heavy for it.

If you would want to build a spin of flashback, here's the basic receipe:

mini.iso
xinit (I use startx instead of a DM)
xserver-xorg or just xorg
gnome-session-flashback --no-install-recommends
synaptic

And your off and running :)

also

[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)

[COLOR=#ff0000]EDIT[/COLOR]   Panels and some windows will be black on black at the start, adjust the background color.

---

### Post by windowsfree on 2014-04-21
Thank you.  I appreciate your input very much.

---

