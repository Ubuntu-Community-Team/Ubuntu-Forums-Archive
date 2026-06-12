---
title: "Ubuntu Widgets Available?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by thordiddy on 2006-06-22
The other day I was browsing a random site and saw a Ubuntu screenshot where a user had what appeared to be widgets installed on his desktop.

These included a system monitor and a hard disk monitor that would indicate how much free space was left.

I lost the URL with the screenshot and cannot figure out where to find such applications.

Any ideas? Thanks.

---

### Post by Xzallion on 2006-06-22
install gdesklets using synaptic or this code. 
```
sudo apt-get install gdesklets
sudo apt-get install gdesklets-data
killall gnome-panel
```
then find Applications>Accessories>GDesklets in your menu.

---

### Post by confused! on 2008-02-09
Once you've got the shell, where do you get the widgets from?
Cheers.

---

### Post by Mary.Riley on 2008-02-09
Most of the desklets come preinstalled with the 'sudo apt-get install gdesklets-data' command.

This website is a great place to start (and maybe finish) for Desklets:

[http://www.gdesklets.de/](http://www.gdesklets.de/)

---

### Post by macogw on 2008-02-09
I'd recommend [Screenlets](http://screenlets.org).  GDesklets are annoying because they are either in front of or behind a window and you can only get them back by minimizing the window.  Screenlets can be set as "widget" type so that the Widget Layer in Compiz controls them.  You set a key in Compiz to hide/show the Widget Layer, and all of a sudden you've got the OSX Dashboard (background dims, widgets appear floating on top, etc).

---

### Post by yizuman on 2008-02-09
> **macogw said:**
> I'd recommend [Screenlets](http://screenlets.org).  GDesklets are annoying because they are either in front of or behind a window and you can only get them back by minimizing the window.  Screenlets can be set as "widget" type so that the Widget Layer in Compiz controls them.  You set a key in Compiz to hide/show the Widget Layer, and all of a sudden you've got the OSX Dashboard (background dims, widgets appear floating on top, etc).

I got the screenlets-0.0.10.tar.bz2 file downloaded from the [http://screenlets.org/index.php/Download](http://screenlets.org/index.php/Download) website and I am having trouble understanding (I'm a newb of course) where do I extract these files into and make it work? The readme file is kinda confusing.

Thanks in advance,

Yiz

---

### Post by dark_phantom on 2008-02-09
> **yizuman said:**
> I got the screenlets-0.0.10.tar.bz2 file downloaded from the [http://screenlets.org/index.php/Download](http://screenlets.org/index.php/Download) website and I am having trouble understanding (I'm a newb of course) where do I extract these files into and make it work? The readme file is kinda confusing.

Thanks in advance,

Yiz

If you're asking about installing screenlets that are not part of the initial install.  Then, you have to extract them to the /usr directory where screenlets reside.  I forget the exact path to where you have to install them.  Do a find command to find where it is at, find /usr -name 'screenlets' -print.

---

### Post by szekelyrobi on 2008-02-09
You just have to extract into a folder to your hard drive than run Synaptic go to File than Add downloaded packages than locate the folder and add and your done screenlets will appear in your accessories.I hope it helps you!

---

### Post by rainwalker on 2008-02-10
Screenlets are far better than gDesklets, and there are way more of them.

To install screenlets, download the deb from [http://www.gnome-look.org/content/show.php?content=73346](http://www.gnome-look.org/content/show.php?content=73346)
Then go to System > Preferences > Screenlets and have fun.
To install more of them, just download them from [www.gnome-look.org](www.gnome-look.org) (save them to your desktop) and then go into the screenlets window and click the install button, and go to the screenlet you just downloaded.
For each screenlet you can edit it's settings by right-clicking on it

---

### Post by fracturedmorals on 2008-02-10
To install a new widget into the screenlets program, create a .screenlets/ directory in your home folder....then just extract the tarball to that folder.

---

