---
title: "Removed Unity - everything's gone?"
date: 2012-04-08
forum: Desktop Environments
---

### Post by L.E.n on 2012-04-08
Hey. I've just installed Ubuntu 10.10 and updated it to Natty accordingly, which means I've gotten Unity installed in the end. I've attempted to remove Unity following a manual on Ubuntu.cz Wiki, though after I rebooted the system, I had just a blank desktop.

Is it possible to somehow get it working just like it was at 10.10 without Unity? Do I need to reinstall GNOME Environment or something...? Thanks in advance.

It looks like [this]("http://img822.imageshack.us/img822/9369/obrazovkaw.png") now, by the way.

---

### Post by 23dornot23d on 2012-04-08
Ctrl + Alt + F2

Login to the console and type in
[B]
sudo apt-get update

sudo apt-get install gnome-shell[/B]

or if you want something else let us know ....

you can load in LXDE XFCE E17 of KDE ....... or something else there are others
but these are the more popular desktops available

> 

for KDE

sudo apt-get install kde-full




---

### Post by zombifier25 on 2012-04-08
Try looking at the bottom panel at the login screen and select Classic Session from the Session menu (I haven't used 11.04 for a while, so the menus' name are probably not exactly like this)
> **23dornot23d said:**
> Ctrl + Alt + F2

Login to the console and type in
[B]
sudo apt-get update

sudo apt-get install gnome-shell[/B]

or if you want something else let us know ....

you can load in LXDE XFCE E17 of KDE ....... or something else there are others
but these are the more popular desktops available
No.
1. gnome-shell is not in the Natty repos.
2. I don't think this is the best solution.

---

### Post by L.E.n on 2012-04-08
I don't get the sessions menu since I removed Unity, so I guess that would not be possible.
Also, I have 10.10 originally, so I might try what 23dornot23 said, thanks.

---

### Post by 23dornot23d on 2012-04-08
You can also look for install other desktops via command line ..... [[COLOR=Blue]_**LINK**_[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=install+XFCE+command+line&ie=utf-8&oe=utf-8")

Detailed instructions are given in most cases .... but if you need any help
just pop a message back .....

[IMG]http://img594.imageshack.us/img594/1518/snapshot6w.jpg[/IMG]

I am happy with KDE now .... and the latest version of it is very good .... this will be coming out soon
near the end of the month ..... if you want to upgrade later on .......

---

### Post by 3Miro on 2012-04-08
@23dornot23d: there is no Gnome-shell on 11.04 Natty.

@L.E.n: 11.04 comes with Gnome 2 and Unity running on top of Gnome 2. If you want the old interface, all you need to do is login using "ubuntu classic" mode. There is no point in removing Unity as it takes so little space on your HDD. To restore your system, you can use:
```
sudo apt-get install ubuntu-desktop
```

If you want to try other environments, you can look at the psychocats tutorial:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Make sure you are reading the instructions for 11.04 and not some of the newer releases (i.e. 11.10 or 12.04 Beta).

---

