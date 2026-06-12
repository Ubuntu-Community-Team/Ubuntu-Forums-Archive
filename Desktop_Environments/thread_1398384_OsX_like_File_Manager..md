---
title: "OsX like File Manager."
date: 2010-02-04
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-04
Hi all, Is there a file manager for Linux like the one of OsX with more than 4 panes for exploring contents of subfolders and for previewing the files in the next pane ?

Thanks in advance.

---

### Post by kellemes on 2010-02-05
Have you looked at the dualpane filemanagers?
A couple of samples..
[krusader]("http://www.krusader.org/") (have used it in the past, comparable with Total Commander for Windows, very powerful)
[worker]("http://www.boomerangsworld.de/worker/") (ugly but extremely powerful)
[mc]("http://www.midnight-commander.org/")
[Gentoo]("http://obsession.se/gentoo/")
[emelfm]("http://emelfm.sourceforge.net/")
[mucommander]("http://www.mucommander.com/")
[Gnome commander]("http://www.nongnu.org/gcmd/")
etc..

More about Ortodox filemanagers.
[http://www.softpanorama.org/OFM/index.shtml]("http://www.softpanorama.org/OFM/index.shtml")

---

### Post by hariks0 on 2010-02-05
Great file managers they are but still these are only dual pane. I needed one with more sub-panes until it reaches the innermost folder. The last pane would be the preview of the selected file.

Thank you for your feedback.

---

### Post by hainen on 2010-02-06
Try with Dolphin or Konqueror. They have a view mode called "Columns" ( Ctrl+3 is the shortcut )

---

### Post by hariks0 on 2010-02-06
Thank you hainen, It was exactly what I was looking for. Dolphin is great. Can you please tell me how the look and feel could be customised to match gnome. Now the Places menu is brown and the contents in dolphin are blue. Also please tell me how I can use the Nautilus scripts in Dolphin.

---

### Post by hainen on 2010-02-06
> **hariks0 said:**
> Thank you hainen, It was exactly what I was looking for. Dolphin is great. Can you please tell me how the look and feel could be customised to match gnome. Now the Places menu is brown and the contents in dolphin are blue. Also please tell me how I can use the Nautilus scripts in Dolphin.


I'm not completely sure, but I think Nautilus scripts is similar to "Service Menu" in Dolphin and Konqueror.
To get a more uniform look you could try QGtkStyle.

---

### Post by hariks0 on 2010-02-07
> **hainen said:**
> I'm not completely sure, but I think Nautilus scripts is similar to "Service Menu" in Dolphin and Konqueror.
To get a more uniform look you could try QGtkStyle.

I was not able to ind a 'Service Menu' in both. also how can I use the qgtkstyle. I am using dolphin in gnome but have kde and xfce in addition to gnome.

Thank you.

---

### Post by Perfect Storm on 2010-02-07
> **hariks0 said:**
> Thank you hainen, It was exactly what I was looking for. Dolphin is great. Can you please tell me how the look and feel could be customised to match gnome. Now the Places menu is brown and the contents in dolphin are blue. Also please tell me how I can use the Nautilus scripts in Dolphin.

Dolphin is a KDE app that uses QT engine, that's why it doesn't match Gnome (that uses GTK2 engine).

---

### Post by hainen on 2010-02-07
> **hariks0 said:**
> I was not able to ind a 'Service Menu' in both. 

I'm not sure what you mean? But this explains how it works [http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus](http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus)
ant this is a easy to use applet to create them (I have not tried this) [http://www.kde-apps.org/content/show.php/Service+Menu+Editor?content=85062](http://www.kde-apps.org/content/show.php/Service+Menu+Editor?content=85062)

> **hariks0 said:**
> also how can I use the qgtkstyle. I am using dolphin in gnome but have kde and xfce in addition to gnome.

Thank you.

( I only have ubuntu on my server and have Arch with kde on my desktop so I'm rusty on gnome and maybe this is obsolete. ) But when I used Gnome last time with Ubuntu I downloaded and compiled this [http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)
Today, I suppose it exist a Deb package in the repositories, but I don't now the name on that.
An another solution you could try is Qtcurve [http://www.kde-look.org/content/show.php?content=40492](http://www.kde-look.org/content/show.php?content=40492) but I don't now how it works with gnome as main desktop.

---

