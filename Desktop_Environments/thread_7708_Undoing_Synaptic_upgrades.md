---
title: "Undoing Synaptic upgrades?"
date: 2004-12-10
forum: Desktop Environments
---

### Post by Grey on 2004-12-10
I'm a bit of a Linux newbie, I must admit.  But I've been using the development branch of Hoary anyways, as I wanted to use the latest VLC (I couldn't get it compiled), and some other stuff.  And I figured I may as well upgrade the works.

It was working good a few days ago, but I made another mass update today, and it uninstalled Gnome and whatever was making my wireless network card work (Atheros).  KDE is nice and all, but I had Gnome playing nice with XMMS, and I really want my NIC working again, so I just want to backtrack my changes.

I've searched the forum, and I can't find any threads about undoing changes in Synaptic.  I found the commit log that shows my changes, but I don't want to manually go through the list undoing each one, and I don't have internet access anymore without my wireless card... so I can't download the packages either.  (and when I tried to install gnome from the cache, that didn't work either, as it was complaining about missing dependencies.  I would assume that gnome is broken on the development branch).

So... basically I would really appreciate it if someone could tell me a nice easy way of undoing the damage I did.  I could wipe my Linux partition and reformat, but I would rather just repair what I did, as I had Ubuntu behaving quite nicely a couple of hours ago, and I have to say that it's my favorite Linux distro so far.

Thank you very much.

---

### Post by randy on 2004-12-10
The only way that I know of is installing the packages in /var/cache/apt/archives with dpkg.  Or you can download the good packages and install them to.

---

### Post by Grey on 2004-12-11
I was hoping for someone to post an easy fix.  But I guess that's not going to happen.  :(  Ah well, I'll just reinstall Ubuntu tomorrow at some point.  Thanks for the help anyways.

Lesson learned...  don't be careless about installing packages from the development branch.  :)

---

### Post by ubuntu_demon on 2004-12-11
[QUOTE=Grey]I was hoping for someone to post an easy fix.  But I guess that's not going to happen.  :(  Ah well, I'll just reinstall Ubuntu tomorrow at some point.  Thanks for the help anyways.

Lesson learned...  don't be careless about installing packages from the development branch.  :)[/QUOTE]
 Yeah reinstalling is the best option especially since you don't have an internet connection.

Unly use hoary when you can afford the risk of breaking the system.  I wouldn't recommend running hoary for newbies.

If you need a new package install it from source or look for a backport. I wouldn't recommend other ways like apt-pinning for newbies.

Usually go to the website of the application,download the source and do :
sudo ./configure
sudo ./make install 
Ask for more on this if you would like to know or search the forum.

The unofficial ubuntu starters guide is great place for you to learn some basic stuff :
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Good luck and have fun with Ubuntu!

---

### Post by Grey on 2004-12-12
well, I'm a newbie, but not THAT big of a newbie.  ;)  I really wanted to get VLC 0.8 or later working.  I tried for a good half a day to get it compiled, and in the end I just gave up.  (I'm apparently not the only one having difficulties getting it compiled on Ubuntu either)  I think next time I'm just going to stick with Warty, and then install specific packages from Hoary that I want.  (Like VLC.. and some other stuff that escapes me at the moment).  

But thanks again for your attention.  :)

(I should really have a look at the Synaptic source code at some point and see if it's within my capability to write a patch that allows a user to undo changes... seems to me that it would be a handy thing to have)

---

