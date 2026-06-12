---
title: "VNC Ultra-Slow"
date: 2012-05-09
forum: Desktop Environments
---

### Post by N74JW on 2012-05-09
Hello,

I have Ubuntu 12.04 running on some decent hardware. I would like to connect to it over VNC from my Mac (OS X 10.7) using vnc://IP_Address from the command + k dialog. The connection works, unencrypted, albeit very slowly. Is there a way to secure it, in the manner of MS RDP and speed it up (significantly)? Can Ubuntu run MS RDP?

---

### Post by HarvesterOfBeer on 2012-05-12
I have a similar setup and find it to also be very sluggish. One thing that will help is using Chicken instead of the Screen Sharing app to connect to the VNC session. 

[http://www.macupdate.com/app/mac/36208/chicken]("http://www.macupdate.com/app/mac/36208/chicken")

VNC performance is still far below what I had with 10.10 running on the same server.

---

### Post by philhughes on 2012-05-13
Is it generally slow or is it just window redrawing? There are some long-standing bugs on launchpad with window redraw on launchpad. Try using Unity 2D. Unfortunately it appears that Unity 2D will be dropped for 12.10, so I hope these bugs are fixed first.

---

### Post by HarvesterOfBeer on 2012-05-13
How to switch to Unity 2D?

---

### Post by Azyx on 2012-07-10
> **HarvesterOfBeer said:**
> How to switch to Unity 2D?

Log out, and when the login window appear, click the Ubuntu-symbol near then password box, and you can choice 'Ubuntu 2D, I think.

---

