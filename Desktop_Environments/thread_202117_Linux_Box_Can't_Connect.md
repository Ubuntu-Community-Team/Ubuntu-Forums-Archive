---
title: "Linux Box Can't Connect"
date: 2006-06-22
forum: Desktop Environments
---

### Post by MountainMan on 2006-06-22
Howdy

This is my first post...  I;ve got what I hope is a simple question.

I have a home network that consists of wired and wireless, apple pc and linux boxes.  I have one ubuntu box that won't connect to the internet  I can ping the router, firewall and modem all successfully.  I can also access this computer from the "outside" (ie, internet) via ssh.  That is why I'm lost.... I can connect into the box from the outside or within my lan.  I can vnc to or from the box while within my lan.  But, for some reason I can not get that box outbound.

Can anyone help?

RJ

---

### Post by will_in_wi on 2006-06-22
What does the commandline say when you ping [www.google.com?](www.google.com?)

---

### Post by MountainMan on 2006-06-22
From that machine I get:

$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

From any other machine on the lan, I get the normal pings showing, and o% loss.

It's like it (the ubu box) is not connected at all.  But I can ssh into it....

Thanks

---

### Post by MountainMan on 2006-06-22
Got it!  My DNS Servers had been deleted, and that caused the funny behavior

Thanks to all

---

