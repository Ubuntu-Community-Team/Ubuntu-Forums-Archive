---
title: "Tight vnc, no menu or desktop items"
date: 2008-02-18
forum: Desktop Environments
---

### Post by DanielReidal on 2008-02-18
I have re-installed ubuntu on my box. Before I had a functional tight vnc server installed. No problems a all.

But now I have some problems.

1. I usually connected to the server with "drserver :1", but now I need to connect using its ip (192.168.0.100 :1)
2. This is the really problem. When I connect I can just see the mouse pointer and a terminal window. No other desktop items like the menu.

I have just followed the VNC guide in the community docs, but this time it does not work. 

Any ideas?

Cheers Daniel

---

### Post by klo on 2008-05-17
Try something like this:
```
Xtightvnc :1 -geometry 800x600 -query localhost -once -depth 24 -localhost
```

then connect with:
```
vncviewer 127.0.0.1:1
```

Since I tunnel this using SSH, you will need to remove "-localhost" (and others?) and change the IP address you connect to.

The trick is not to use the tightvncserver script - took me a day to figure this out...

---

