---
title: "Bit Torrent 4 Official problems"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Kokanee on 2005-10-25
I'm on Breezy.  I downloaded the stable tar.gz [Bit Tornado]("http://www.bittornado.com/download.html") (for the GTK2 support) and was using it with no problems.  I decided to try out the Official Client.  I downloaded the [Python 2.3 DEB]("http://www.bittorrent.com/") from the official web site.  It installed fine.  However when I run btdownloadgui.py I get the following error message:

```
colin@ubuntu:~$ /usr/bin/btdownloadgui.py
Traceback (most recent call last):
  File "/usr/bin/btdownloadgui.py", line 33, in ?
    from BitTorrent import configfile
ImportError: cannot import name configfile
``` 
Any ideas?

---

### Post by stoeptegel on 2005-10-25
My experience by installing them with synaptic, is that mainline and bittornado byte each other. So i just use one of both, bittornado cause i hate that "have you donated" question in mainline. (on trackers without a whitelist for clients i use rufus though)

---

### Post by Kokanee on 2005-10-25
Thats the problem I think.  But the Bit Tornado was installed from maunally from a tar.gz.  So I'm not to sure of what files to go and delete? :???:

---

### Post by thumbsoup on 2005-10-25
I had problems with the deb install of BitTorrent 4.1.6 as well, and the advice I got on this forum worked for me.  You can search the forum with the number 4.1.6, or just look at the link below. 


[http://www.ubuntuforums.org/showthread.php?t=80361&highlight=4.1.6]("http://www.ubuntuforums.org/showthread.php?t=80361&highlight=4.1.6")

---

### Post by Kokanee on 2005-10-25
Ok. Fixed! I made sure those packages were installed (which they were) and made sure the Regular Bit Torrent 3.x package was removed. Then I tried the 4.1.6 DEB rather than the 4.0.4 DEB and now it works! :D

---

