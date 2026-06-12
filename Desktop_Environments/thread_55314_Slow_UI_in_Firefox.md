---
title: "Slow UI in Firefox"
date: 2005-08-08
forum: Desktop Environments
---

### Post by Shusaku on 2005-08-08
I recently installed Kubuntu 5.04 on my wife's PC and it seems quite nice.  The only problem so far is that Firefox (1.0.6) is very sluggish and unresponsive.  For example, whenever I click one of the menus at the top (Bookmarks, Tools, etc) it takes perhaps 2 seconds before it actually responds.  The actual web pages load relatively quick but the UI just feels so slow and jumpy (draggy?).  All other apps run much more smoothly.

The box is a P3/600 with 256M RAM and a 30GB HD.  I've already made all the suggested Firefox tweaks related to IPv6, pipelining, etc.  I've also tried running XFCE, IceWM, even Gnome, but Firefox was equally slow under all of them.

Is Firefox just slow on Linux with this hardware, or are there other config changes to try (we don't want to switch browsers).  It was much more responsive under Windows 2000.  But I really want to stick with Linux/Kubuntu.

Thanks in advance!

---

### Post by shakin on 2005-08-08
Hit Ctrl-Esc to open KDE System Guard and keep your eye on which process(es) use a lot of CPU or RAM that might make Firefox slow.

I also suggest looking to see what things are running on startup that can be removed.

You can also try installing it from the Firefox web site (install into /opt/firefox so it doesn't take over from the Ubuntu package). Maybe there is a difference. You can also try out the Deer Park alpha if you want because it has a lot of performance improvements.

---

### Post by daigorobr on 2005-08-08
[QUOTE=shakin]Hit Ctrl-Esc to open KDE System Guard and keep your eye on which process(es) use a lot of CPU or RAM that might make Firefox slow.

I also suggest looking to see what things are running on startup that can be removed.

You can also try installing it from the Firefox web site (install into /opt/firefox so it doesn't take over from the Ubuntu package). Maybe there is a difference. You can also try out the Deer Park alpha if you want because it has a lot of performance improvements.[/QUOTE]

In fact, I noticed a great improvement in Firefox speed with Deer Park - even tho it hogs the same amounts of resources than 1.0.6.

---

### Post by varunus on 2005-08-08
Firefox seems plenty fast to me; perhaps try running it from a terminal and see if you get any errors that could be causing slowdown?

I can see why it might be slow under KDE, since Firefox uses the GTK toolkit to render, but under GNOME it should be fine.  Its fine for me...how fast is the computer?

---

### Post by Lord Illidan on 2005-08-08
Funny, I just installed Debian Sarge, Firefox on it is faster than on Kubuntu....could it be because of the damn GTK interface? But I was using KDE at that time..

It is also faster on Windows....

---

### Post by JLTB on 2005-08-10
Firefox is a very good browser; however, on such a low end machine (no offence in anyway .. i've got a couple myself) have you considered using a different browser?

Maybe give Opera a shot (its got a rep for being pretty quick), Konqure is okay (imho, it breaks too many pages).

---

### Post by FNM on 2005-08-12
I find Firefox to be quite sluggish on Linux as well. I've been using Opera, and I love it. It's much, much faster, and more responsive than Firefox. Check out these speed comparisons. [http://www.howtocreate.co.uk/browserSpeed.html](http://www.howtocreate.co.uk/browserSpeed.html)

---

### Post by Mishura on 2005-08-13
I found the Firefox version in Backports to be **hella** slow.  So slow, in fact, that I uninstalled it and installed the official one from Mozilla.org.  That version is **twice** as fast as the Hoary Backports one.   Backports FireFox also had many issues with some of my extensions like Flashblock and a few others.  Mozilla.org Firefox fixed these, however.

As soon as Konqueror gets adblock, and a defined extensions system, I'll probably quit Firefox for Konqui.  It's way faster than FF and Opera 8.

---

