---
title: "bad bencoded data"
date: 2006-08-19
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-19
I used Dapper, and I didn't like it, so now I am using 5.04 Hoary. There is a problem using torrents. I've tried 10 torrents so far and each one is saying the same thing "ERROR - bad bencoded data" If this only happened once or twice, I would say it is something wrong with the torrent or tracker, but this has happened with many torrents from different websites.

---

### Post by FRealmS on 2006-09-06
Hi, i used Ubuntu Dapper and i have the same problem... ](*,) 
but i found the answer... i remove the package *bittorrent* version 3.xx.xx... then apt-get say that the other two packages must be removed *gnome-btdownload* and *ubuntu-desktop*... then i download the deb package bittorrent from [http://www.bittorrent.com/download.html]("http://www.bittorrent.com/download.html")
version 4.20.9
and all is done :D 

Enjoy :twisted:

---

### Post by fakie_flip on 2006-09-06
> Hi, i used Ubuntu Dapper and i have the same problem... ](*,) 
but i found the answer... i remove the package *bittorrent* version 3.xx.xx... then apt-get say that the other two packages must be removed *gnome-btdownload* and *ubuntu-desktop*... 

Removing ubuntu-desktop does not cause a problem? What do you do without Ubuntu Desktop, use the command line?

> then i download the deb package bittorrent from [http://www.bittorrent.com/download.html]("http://www.bittorrent.com/download.html")
version 4.20.9
and all is done :D 

Enjoy :twisted:

That package is for Debian and not Ubuntu correct? You may find some problems or not know why you have errors later because of that. Ubuntu packages and Debian packages are not the same and are supposed to cause problems when not used on the distrobution they were made for. I will probably go to that website and get the deb anyways because I have Debian Etch testing unstable now, and I am liking it a whole lot better than Ubuntu. It's nice to have newer versions of software too instead of having old ones that are in Ubuntu repositories.

---

### Post by FRealmS on 2006-09-12
hmmm, ...

*first - my english is bad* :roll: 

...i don't know what is the difference between *bittorrent in ubuntu repositories* and *debian package bittorrent* ... maybe different developers...
but for now i don't have any problem with this version... seed, leech, and others! Before i probe with few clients - *qtorrent, rtorrent, bittornado*. They all are in ubuntu repos... and with all i have the problem with "tracker error: bad bencoded data"... 

This is the first torrent client that work in my system with Ubuntu 6.06

> *[COLOR="Red"]ubuntu-desktop[/COLOR]*

The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is [COLOR="Red"]safe to remove[/COLOR] this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).
> *gnome-btdownload*

Gnome interface for 'executing' BitTorrent files
A simple Gnome interface designed as a mime-sink for BitTorrent files.

Not a front-end, more-or-less just a session dialog. See bittorrent
for more information.

Homepage: [http://gnome-bt.sourceforge.net/](http://gnome-bt.sourceforge.net/)
I don't know why apt-get want to remove ubuntu-desktop
> sudo apt-get remove bittorent
> Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  bittorrent gnome-btdownload ubuntu-desktop
...

And after this ... my system work **_perfect_**... i don't lose Gnome Desktop!!! :)

Enjoy :twisted:

---

### Post by fakie_flip on 2006-09-14
Okay, thanks very much for the information. I have one more question. How can we use bittorrent from the command line? Try this:

```
bt<tab><tab>
```

and you will see lots of bittorrent commands. Even the bittorrent package does not include a GUI. Only the package bittorrent-gui does. I sometimes put my computer into runlevel 3 while I am not using it or boot into runlevel 3. I've read many man pages, but no help yet. Thanks.

---

