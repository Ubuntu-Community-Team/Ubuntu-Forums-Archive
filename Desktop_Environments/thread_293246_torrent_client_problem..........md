---
title: "torrent client problem........."
date: 2006-11-04
forum: Desktop Environments
---

### Post by ronj on 2006-11-04
hey guys i am new to linux and just installed new version of ubuntu.
i want to use azureus 4 dwnldng torrents .
i installed it thru package manager and also dwnlded it frm azureus.siurcefirge.net
but as soon as i strt azureus my computer enters dead state(ie hangs)
it means i am nt able to opn any othr appln aftr dis.
i cnnt even open a terminal.
hv to directly strt computer by switching off power supply.
plz helpm e into dis.

---

### Post by taurus on 2006-11-04
Do you have java installed on your machine since azureus needs java?  Otherwise, you can always check out the new torrent client called deluge...

[http://www.ubuntuforums.org/showthread.php?t=289237](http://www.ubuntuforums.org/showthread.php?t=289237)

---

### Post by ronj on 2006-11-05
i tried installing deluge but gt d error 
(deluge.py:6478): Gdk-WARNING **: locale not supported by Xlib

(deluge.py:6478): Gdk-WARNING **: cannot set locale modifiers
Traceback (most recent call last):
  File "deluge.py", line 39, in ?
    import torrent
ImportError: No module named torrent

---

### Post by zek725 on 2006-11-05
**Bittornado** works just fine with me.

```
sudo aptitude update && sudo aptitude install bittornado bittornado-gui
```

---

### Post by ronj on 2006-11-06
i hv bittornado installed.
my problem with it is tht i gt low spds in it.
also i mostly dwnld frm pvt tracker ie hvng ratio restrictions.
it does nt report correct statistics to d tracker.
hence i wntd azureus.
plz sumbody help me in installing azureus.

---

### Post by taurus on 2006-11-06
Try using Automatix2 to install azureus.  Also, make sure you don't have any firewall running and if you are using a router, check the ports...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by caseymoore on 2006-11-06
The bittorrent client that comes with ubuntu seems to work best for me.
All the other bittorrent clients seem to mess up.

Azureus: A small box sits at the bottom right hand side of the screen, no matter what you do this little box will not go away.

Ktorrent: No one ever seeds when I use this client for some reason.

---

### Post by vogelaarke135 on 2006-11-06
Hi guys, I have got the same problem,I'm on Edgy:
When I try to download a torrent (the default client, bittornado, deluge, whatever, it doesn't matter) my computer completely freezes! The only thing I can do is a hard reboot (like I'm back on win XP) ](*,)   . It seems to be a problem with wireless connections and torrents, even in other distro's, but also Edgy (last post): [http://www.linuxforums.org/forum/suse-linux-help/67790-p2p-torrent-hangs-suse-10-10-1-a.html](http://www.linuxforums.org/forum/suse-linux-help/67790-p2p-torrent-hangs-suse-10-10-1-a.html). But I haven't got a solution yet.

---

### Post by killjoy966 on 2006-11-14
I seem to be having the same problem as **vogelaarke135**. I suppose it warrants mentioning that I too have a wireless connection. Has anyone made any progress towards finding out if this is the problem?

---

