---
title: "bittorrent not working"
date: 2006-06-30
forum: Desktop Environments
---

### Post by antoxa on 2006-06-30
Hello! i installed bittorrent client from [http://www.bittorrent.com](http://www.bittorrent.com) and get following error message: bash: /usr/bin/bittorrent: /usr/bin/python2.3: bad interpreter: No such file or directory any ideas how to fix it?
:roll:

---

### Post by atoponce on 2006-06-30
[quote=antoxa]Hello! i installed bittorrent client from [http://www.bittorrent.com]("http://www.bittorrent.com") and get following error message: bash: /usr/bin/bittorrent: /usr/bin/python2.3: bad interpreter: No such file or directory any ideas how to fix it?
:roll:[/quote]

How did you install it?  The best way to install software is through Applications --> Add/Remove.  Browse to the Internet category, and you will see BitTorrent.  It is installed by default.

This means that you should have BitTorrent under the Applications --> Internet menu.  If not, pull up Applications --> Accessories --> Alacarte Menu Editor and add it.

---

### Post by antoxa on 2006-06-30
i downloaded deb package from bittorrent.com

---

### Post by ngnr on 2006-07-01
Hi, i had the same problem. this is how i fix it.

1) remove current bittorrent using synaptic or apt-get.

2) go to :
 [http://download.bittorrent.com/dl/?M=D](http://download.bittorrent.com/dl/?M=D)

3) download :
bittorrent_4.20.0_python2.4.deb  ( for python 2.4 )
or
bittorrent_4.20.0_python2.3.deb  ( for python 2.3 )

versions 4.20.1 and 4.20.2 didn't worked for me.

try to open bittorrent using command line because package does not install a menu entry. 

sorry for my english. 

good luck. ;-)

---

### Post by deathbyswiftwind on 2006-07-01
I prefer azureus for its many options you should check into it its a very nice powerful bittorrent client

Cool features

Only download the files you want out of the torrent
Limit Download and upload rate of each torrent
All in one window instead of many little windows

---

