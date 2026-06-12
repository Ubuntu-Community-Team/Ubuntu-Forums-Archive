---
title: "How to compile whah ?"
date: 2009-01-08
forum: General Help
---

### Post by ckata on 2009-01-08
Hey everyone,
I'm looking for a good window manager and my initial research points to whah. I downloaded it but have no idea how make and install it.

You're help is greatly appreciated!

Cheers,
Chris

---

### Post by x22 on 2009-01-08
welcome to the forum

> whah

? spelling.  Found no such window manager

---

### Post by ckata on 2009-01-09
> **x22 said:**
> welcome to the forum

> whah

? spelling.  Found no such window manager
you can find it here [http://repetae.net/computer/whaw/](http://repetae.net/computer/whaw/)

---

### Post by steveneddy on 2009-01-09
> **ckata said:**
> you can find it here [http://repetae.net/computer/**whaw**/]("http://repetae.net/computer/whaw/")

[COLOR=Blue]wha[/COLOR][COLOR=Red]**w**[/COLOR]

So, what's so good about this as opposed to other window managers?

Does the folder you extracted have a read me file?

Does that read me file tell you how to install it?

---

### Post by ckata on 2009-01-09
> **steveneddy said:**
> [COLOR=Blue]wha[/COLOR][COLOR=Red]**w**[/COLOR]

So, what's so good about this as opposed to other window managers?

Does the folder you extracted have a read me file?

Does that read me file tell you how to install it?

That's a good question. I don't know if it's better or worse. It's just that the reading i did seemed to point to this one. 

There is a readme but with no information on making the install nor is there any on his website. I guess he just assumed people would know how to make it!

If you can remcommend an alternative I'm all ears !

---

### Post by steveneddy on 2009-01-10
I looked here:

[http://xwinman.org/](http://xwinman.org/)

and didn't see any mention of this so called

[B]whaw
[/B]
What's wrong with Gnome, Metacity, KDE, XFCE, Fluxbox and Enlightenment (the main WM's used with Ubuntu?

---

### Post by ubootfanat on 2011-02-22
for those which are still interested and got here through google (as I did):

**what is whaw**
[LIST]
[*] integrates with gnome and metacity on ubuntu 10.04 LTS quite nice (this is what I am running here)
[*] allows you to select a couple of windows and fit them to maximum size either on the screen or in a box
[/LIST]

**build v0.1.2**
[LIST]
[*] as usual use ./configure and resolve missing dependencies (apt-file find <missing file> helps a lot)
[*] make
[*] it seems that the latest configure file does not check all dependencies. so you might get errors here as well. look for the missing files and install the corresponding packages (again apt-file is your friend)
[*] after you are done there is an executable in your current directory called "whaw"
[/LIST]
[B]
run[/B]
[LIST]
[*] just run ./whaw
[*] no move your cursor in the top left corner of your desktop
[*] click on two or more windows (they will get minimized)
[*] use your right mouse button
[*] whaw!
[/LIST]

rtfm, the README or the website ([http://repetae.net/computer/whaw/](http://repetae.net/computer/whaw/)) for more info about usage

ubootfanat

---

