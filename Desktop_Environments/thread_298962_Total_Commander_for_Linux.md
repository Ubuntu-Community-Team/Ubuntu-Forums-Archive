---
title: "Total Commander for Linux"
date: 2006-11-13
forum: Desktop Environments
---

### Post by Belgatom on 2006-11-13
I have been looking for a good filemanager. Nautilus does what it's supposed to do, but I am used to a Total Commander type interface. I have found [Krusader]("http://krusader.sourceforge.net/index.php") but this is package optimized for KDE. Is there something in the resources like Krusader (and that looks that yummy)? 

Or is it really not very hard to run Krusader on Gnome? 

Oh, and if it supports compressing and uncompressing, that would just be perfect.

---

### Post by FyreBrand on 2006-11-13
Here is a link to the [**Krusader Handbook FAQ**]("http://krusader.sourceforge.net/handbook/faq.html").  It has some interesting info in it.

It says you can run Krusader in Gnome and other desktop environments.  You only need kdelibs and QT to *run* it.  But in order to get fuller functionality you need KDE base and especially KIOslaves.  But you don't need to login using the KDE window manager.

That sounds nice in theory, but I don't know how practical it is in reality.  Sometimes I have had real problems running some KDE apps in Gnome and less so Gnome apps in KDE.  Usually they work okay, but sometimes they just break really bad.

Give it a shot and report back.  I would be curious to know how it works out.  Wouldn't it be great if KDE and Gnome played better together?

---

### Post by atery on 2006-11-13
I've got the same question when I first turned to ubuntu from windows. I ended up with using "Tux Commander" instead of trouble Krusader, although this software is less functional than TC.

---

### Post by skymt on 2006-11-13
A lot of people like [Gnome Commander]("http://www.nongnu.org/gcmd/") (package name: gnome-commander). Midnight Commander (package name: mc) is the best Commander for Linux, but it's terminal-only. Which shouldn't matter, since the entire point of the commander interface is to maximize keyboard use.

---

### Post by adriantry on 2006-11-13
> **atery said:**
> I've got the same question when I first turned to ubuntu from windows. I ended up with using "Tux Commander" instead of trouble Krusader, although this software is less functional than TC.

I like Tux Commander.

There is also emelfm2 ([http://emelfm2.net/)](http://emelfm2.net/)).

Adrian

---

### Post by urukrama on 2006-11-14
Krusader works fine on Gnome here. It misses some functions that require other KDE packages, but just for general file browsing/deleting/searching/... etc it works fine. I don't know about accessing files over a network, as I haven't had to do that yet.

Gnome Commander and Tux Commander are OK, but really lack in functionality and are a bit ugly.

I haven't tried emelfm2 yet. Installing it now -- thanks for the tip.

---

### Post by urukrama on 2006-11-15
By the way, also have a look at [http://www.rmonet.com/commander/#linux](http://www.rmonet.com/commander/#linux)

There are quite a few other options listed there (many of which are no longer developped or maintained).

---

### Post by temcat on 2006-11-15
I think I tried most of two-panel file managers using GTK+ widget set. As for local file management, Gnome Commander is the most full-featured of them. However, it has problems with FTP (which are probably caused by GnomeVFS, not Gnome Commander as such).

---

### Post by NiksaVel on 2006-11-16
I use Krusader under ubuntu with some KDE packages added and it works GREAT...  I am actually happier with it than with the original total commander - a lot happier.

I've tried other solutions like gnome-commander, but somhow feel best with Krusader.

---

### Post by FrankVdb on 2006-11-16
Thanks guys, was looking for something like Gnome Commander too. Nautilus is just dreadful...

---

### Post by urukrama on 2006-11-16
> **FrankVdb said:**
> Thanks guys, was looking for something like Gnome Commander too. Nautilus is just dreadful...

If you just want a normal file manager (not a two paned one): have you tried Thunar? I quite like its lightness and elegance, and use it all the time, except when I have to copy or move files around, for which I prefer a two paned browser.

Also, see the following article on Linux.com on file managers for Linux:

[http://applications.linux.com/applications/05/02/23/2226202.shtml](http://applications.linux.com/applications/05/02/23/2226202.shtml)

---

