---
title: "Help setting up VNC server (with resumeable sessions &amp; restricted to localhost)"
date: 2008-12-13
forum: General Help
---

### Post by theolster on 2008-12-13
I've been messing around with setting up a VNC server for some time, but can't quite get the right information/understanding from the relevant tutorials or man pages to get the setup just how I want it.

I need the following:
[LIST]
[*]Resumable sessions - [this howto]("http://ubuntuforums.org/showthread.php?t=122402") works well, but I can't get it to restrict incoming connections to the localhost only.
[*]Restrict incoming connections to the local host - [this howto]("http://ubuntuforums.org/showthread.php?p=4963842") works well - but not with resumeable sessions!
[*]To be able to use [Chicken of the VNC]("http://cotvnc.sourceforge.net/") as the client software.
[/LIST]

I'm using an 8.04 install and have implemented the second guide, how do I now edit the /etc/xinetd.d/Xvnc to restrict access to local connections?

Many thanks in advance!

---

### Post by theolster on 2009-01-14
Update - I'm still trying to work out how to sort this out, if anyone can help me?

---

### Post by gene02 on 2009-01-22
Use your firewall to restrict connections to localhost.

---

### Post by theolster on 2009-01-23
Thank you very much.
Problem solved.

---

