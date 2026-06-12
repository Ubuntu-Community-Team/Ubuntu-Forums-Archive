---
title: "ubuntu vs. xubuntu (my experience)"
date: 2005-12-26
forum: Desktop Environments
---

### Post by ozziem on 2005-12-26
So I have an old pc (K6-2, 350MHz, 128MB RAM) that I decided to take out from the closet to try (x)ubuntu. After reading advice here and elsewhere, I decided to do the "server" install and then install xubuntu-desktop.

This initially seemed quite good, with no major performance issues. However, xfce soon appeared to begin "misbehaving". I would log in and all my font sizes would be changed, the panel would not start, no desktop background would render, and desktop menu would also be inoperable. Rather than try to discover what was wrong, I just deleted all the config files from my home directory and restarted fresh. However, the problem would always come back - most frustrating. :mad: 

So I decided to bite the bullet and just install regular ubuntu-desktop. I find that gnome works fine on this system and is MUCH more reliable than xfce appeared to be. I honestly do not feel the performance is any slower than I had with xfce. I may try dumping Metacity for something else down the road, since it really doesn't appear to bring anything to the table that other lighter WM's don't have ..... but otherwise, I'm happy! :p 

Anyone else care to share any similar experiences running (x)ubuntu on a similarly old machine?

---

### Post by Maelgwyn on 2005-12-26
yup!

I'm running an old 866MHz with 256MB RAM & a 20Gb HDD, and although I loved Xfce, it kept getting 'buggy' on me too!

So I've come back to Gnome :D

OT: when you mentioned dumping metacity, what do you mean by this? I've seen other people write similar things, but I don't understand..?

---

### Post by Sef on 2005-12-26
My Inpiron laptop (Dell) is 700 MHz, 128 ram and a 10 gb hd.   Ubuntu works fine with it. :)

---

### Post by ozziem on 2005-12-26
> **Maelgwyn]
although I loved Xfce, it kept getting 'buggy' on me too![/QUOTE]

glad to hear it wasn't just me ...  said:**
>  OT: when you mentioned dumping metacity, what do you mean by this? I've seen other people write similar things, but I don't understand..?

Metacity is the window manager that is used by default in ubuntu. Back when I used to run Redhat, the gnome installation used to allow selection of different window managers in the control-center (I think it was called) - could change to enlightenment, blackbox, .... etc. There seem to be several howto's on these forums on how to do the same, but it no longer seems integrated into the gnome graphical settings. For example:
[http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox+howto](http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox+howto)

I guess my thinking is that using something like openbox instead of metacity might free up a little of my limited RAM.

---

### Post by kaamos on 2005-12-26
The xfce in ubuntu repos is in my experience indeed quite buggy. Got sick of it, remove it completely and compiled xfce apps from cvs. The cvs-version worked great, I couldn't even get thunar to crash and that is pre-alpha software! Of course, the amount of apps I compiled was about just the necessary ones, but still this is a very nice setup.

The packages that I compiled were
> gtk-xfce-engine-2 libxfcegui4 libxfce4mcs libxfce4util mousepad xfce-mcs-manager xfce-mcs-plugins xfce-utils xfce4-dev-tools xfce4-icon-theme xfce4-panel xfce4-session xfdesktop xfwm4 xfwm4-themes thunar libexo0.3 xterminal

---

### Post by sciurus on 2005-12-26
I had Ubuntu on a 500mhz laptop with 256mb of RAM. Normally it worked fine, but sometimes menu items and buttons wouldn't respond to clicks for minutes and they would lock up their parent app (this usually happened after I resumed from hibernation). I switched to Kubuntu and found it much snappier on this low-powered machine than Gnome.

---

### Post by harisund on 2005-12-26
Is there a way to remove any graphic intensive operations? In KDE Sytem Properties, I can avoid animation of menus, minimizations etc etc, and after the entire customization, it becomes fast and with almost minimal, or in fact no eye candy. Could I do that in GNOME / XFCE?

---

