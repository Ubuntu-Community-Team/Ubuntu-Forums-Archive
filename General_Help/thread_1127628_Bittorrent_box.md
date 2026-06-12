---
title: "Bittorrent box"
date: 2009-04-16
forum: General Help
---

### Post by blazemore on 2009-04-16
I'd like a server that runs commandline bittorrent software, and has an easy to use WebUI, so I can log in and add torrents from any PC.

Is this easy to set up?

---

### Post by lvleph on 2009-04-16
I would suggest looking at Deluge.

---

### Post by blazemore on 2009-04-16
I use deluge, but does it run from a command-line?
Reason is, I'm using the same PC for a number of servers, including web and NAS, so CPU cycles are at a premium.

---

### Post by sisco311 on 2009-04-16
> **blazemore said:**
> I use deluge, but does it run from a command-line?
Reason is, I'm using the same PC for a number of servers, including web and NAS, so CPU cycles are at a premium.

Yes, deluge>=1.0 does. Add the [ppa repos]("https://launchpad.net/~deluge-team/+archive/ppa") to install the latest version.

[http://dev.deluge-torrent.org/wiki/Faq#Daemon]("http://dev.deluge-torrent.org/wiki/Faq#Daemon")

---

### Post by lovinglinux on 2009-04-16
> **blazemore said:**
> I use deluge, but does it run from a command-line?
Reason is, I'm using the same PC for a number of servers, including web and NAS, so CPU cycles are at a premium.

Deluge 1.1.x can connect to a headless server using cli, remote gtk or web ui. Can't get better than that  ;) 

Take a look at this tutorial:

[http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)

You might also want to read these faqs:

[http://dev.deluge-torrent.org/wiki/Faq#Console](http://dev.deluge-torrent.org/wiki/Faq#Console)
[http://dev.deluge-torrent.org/wiki/Faq#Daemon](http://dev.deluge-torrent.org/wiki/Faq#Daemon)
[http://dev.deluge-torrent.org/wiki/Faq#WebUI](http://dev.deluge-torrent.org/wiki/Faq#WebUI)

---

### Post by blazemore on 2009-04-17
Thanks a lot I will look into that when I get some time.

---

