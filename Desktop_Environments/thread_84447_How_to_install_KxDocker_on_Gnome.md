---
title: "How to install KxDocker on Gnome ?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by TomG on 2005-10-31
Hi 

Does anyone has the way to install KxDocker on Gnome ?
It seems work for Gnome now but instructions on the [[COLOR="RoyalBlue"]website[/COLOR]]("http://www.xiaprojects.com/www/prodotti/kxdocker/main.php") are not fully clear.

Tx
TomG

---

### Post by bk452 on 2005-10-31
[QUOTE=TomG]Hi 

Does anyone has the way to install KxDocker on Gnome ?
It seems work for Gnome now but instructions on the [[COLOR="RoyalBlue"]website[/COLOR]]("http://www.xiaprojects.com/www/prodotti/kxdocker/main.php") are not fully clear.

Tx
TomG[/QUOTE]

Use Synaptic.  It's in there.

---

### Post by TomG on 2005-10-31
Thanks for your reply. But I've already use Synaptic.
My problem is to try to get a complete method. It fails when I try to run it :

[I]root@ubuntu:~# /usr/local/kde/bin/kxdocker
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
kded: cannot connect to X server 192.168.1.4:0
DCOP aborting call from 'anonymous-10756' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
kxdocker: cannot connect to X server 192.168.1.4:0
DCOP aborting call from 'anonymous-10746' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.
[/I]
I have problem with DISPLAY. It also fails with *xclock*. I don't know why, xclock works like this on my Suse.

Tom

---

