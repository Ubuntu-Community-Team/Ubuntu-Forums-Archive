---
title: "Docky Eye Candy for Gnome"
date: 2009-10-23
forum: Desktop Environments
---

### Post by Pauly BC on 2009-10-23
Hi all,

I want to refresh my Ubuntu install to have desktop eye candy like OS-X, along the lines of MoonOS. The default Gnome desktop loaded is a little bit dull like XP. I've been reading through the forums and tutorials and it seems that can be accomplished using several solutions:
Gnome-do
GEUbuntu (Enlightenment)
Kubuntu (KDE though not so much)
Gnome-Shell
Avant WM

Any recommendations on which is more stable/reliable? Any recommendations which can be installed and configured without a black-belt in Sudo?

---

### Post by murderslastcrow on 2009-10-23
The most fast/stable you can get is buy installing e17 from scratch. If you have 32-bit or 64-bit Ubuntu, this should be fairly simple. Just add this source and install e17 with sudo apt-get install e17 in a terminal. [http://packages.enlightenment.org/](http://packages.enlightenment.org/)

Then you can just choose the session when you start up. Some people have reported getting e17 running full speed on 64 MB of RAM, while I can personally say that it runs much much faster than Xfce, but still has the cool effects. This is what is used in MoonOS, but don't expect a lot of window animations.

Another option is to use a dock, and if you're really all into Macs you can use global-menu-applet to make your Gnome bar display the File Menu in any given program up top just like a Mac.

Also, AWN is a big favorite, but sucks up RAM like a big compared to other docks like Cairo. I use Cairo currently, and it's very nice. The only big downside is there are a lot more options (a bit confusing) and it doesn't display Wine program icons like AWN would.

Of course, there are plenty more docks out there to try out, but Cairo and AWN are the most popular/useful you can find (correct me if I'm wrong). Of course, you can customize compiz to add more sexy effects. You can also try dockbarX if you want something like the Windows 7 taskbar.

---

### Post by Shazaam on 2009-10-23
+1 for e17 (Enlightenment). Lxde is good too. DE's (desktop environments) are just about the easiest to install.
[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

Tint2 is neat if all you need is a "window-list" only type of dock. Then put as many launchers/gadgets like kde's plasmoids as you want wherever you want.
[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)

You can also make Metacity a compositing window manager...
[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

Most eye candy puts a config file in your /home folder. No sudo-fu required for tweaking.

---

### Post by Pauly BC on 2009-10-27
I've heard that Enlightenment is still in early development and can be unstable. I don't really want to test that in Karmic.

What about ROX? It seems quite a few people enjoy playing with that?

Rox vs KDE vs Avant - any strong recommendations for Karmic?

---

### Post by VDM on 2009-10-27
Enlightenment 17 is still in development but it has been very stable for a long time as far as i know. 
(Im only checking it out once a while). E17 and EFL are pretty impressive with their modularity and performance. 
Id love to see it around. :D

---

### Post by chiwi on 2009-10-27
Enlightenment is a windown manager for chloe o'brien, not me. I like modern, usable and stylish WM.

-1 for E17

---

### Post by VCoolio on 2009-10-27
> **chiwi said:**
> Enlightenment is a windown manager for chloe o'brien, not me. I like modern, usable and stylish WM.

-1 for E17

Check [here]("http://cafelinux.org/forum/index.php?topic=66.0") for screenshots of e17, a modern, usable and stylish WM. 

If you want docky eye candy for gnome, without changing de / wm, then +1 for tint2 for task list and +1 for cairo-dock if you want an osx-like dock. Sorry for repeating, but I couldn't let the quoted post pass unrebutted ;).

---

### Post by chiwi on 2009-10-28
Looks like I hurt somebody's feelings :)

I used Enlightenment back in my Gentoo days and I really didn't like it for the reasons mentioned above. Perhaps this new E17 has a cool new feature I didn't try.

Thanks for the screenshots, but I'm still not attracted.

PS: yes, I'm an OS X GUI type of guy :popcorn:

---

### Post by Earl_Maroon on 2009-10-28
I have tried various docks, but I eventually settled with Gnome-do. It's not very customisable, but it is responsive, fairly attractive and very reliable. Also, with the default function of Gnome-do as well as the dock interface it's a two in one.

---

### Post by Marrkk on 2009-10-31
u want Mac os X on Gnome Karmic / Jaunty ?

[http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/)

extract & install.. run mac4lininstall.sh 
read and answer questions.. ( enable Metacity compositing - say YES)
search in synaptic for AWN
install all those.
start AWN.. Add the included AWN them in your new mac4lin folder.. apply, prob reboot or logout or restart x server.. you're looking 80% like OS x in just ten minutes. add the wallpaper, its quite convincing..
and u can even do the rest of the tiny tweaks too, once it looks nice ..#
amaze your friends !
hth

---

