---
title: "E1505 will not boot from Ubuntu or Mint Live CD"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by ellandry on 2007-06-12
here are the errors and screens I get, and yes I tried safe graphics mode also.


[http://members.cox.net/ellandry/DCP_7181.JPG](http://members.cox.net/ellandry/DCP_7181.JPG)
[http://members.cox.net/ellandry/DCP_7182.JPG](http://members.cox.net/ellandry/DCP_7182.JPG)
[http://members.cox.net/ellandry/DCP_7184.JPG](http://members.cox.net/ellandry/DCP_7184.JPG)
[http://members.cox.net/ellandry/DCP_7185.JPG](http://members.cox.net/ellandry/DCP_7185.JPG)

Bianca 2.2 livecd loads fine

---

### Post by bunted on 2007-06-12
Can you post /etc/X11/xorg.conf?

---

### Post by ellandry on 2007-06-12
how would i post that when i cant even loag into the live cd? at the prompt? sorry total linux noob here

---

### Post by bunted on 2007-06-12
Why don't you try:

```
ls /etc/X11
```

Look for possibly an xorg.conf.bak or xorg.conf.[a whole bunch of numbers].  If one of those files exist, then you're in luck.  Type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.my.backup
sudo cp /etc/X11/xorg.conf.bak.or.whatever /etc/X11/xorg.conf
```

Type the sudo above if you're not root.  The first command is just a precaution.  Restart and pray.

If you don't have a backup or it doesn't work; you can try:

```
sudo dpkg-reconfigure xserver-xorg
```

That will reconfigure your xserver.  You'll choose resolutions, etc.

If that doesn't work, type:

```
vi /etc/X11/xorg.conf
```

Take some pictures or write down the info, especially the section pertaining to screen and monitor.  ':q' to exit vi.  Try to post that info here.

---

