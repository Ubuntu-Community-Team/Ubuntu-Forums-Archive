---
title: "Thinclient: X forwarding or FreeNX?"
date: 2005-05-17
forum: Desktop Environments
---

### Post by philipacamaniac on 2005-05-17
I want to move my main desktop into my living room to act as sort of a "media server". It has a nice functional Kubuntu install, and eventually I'll be adding MythTV and a tuner card.

But, I still need a computer at my computer desk, for email, web surfing, documents, blah blah. I have an extra Compaq 500Mhz Celeron machine. I want to use it at the computer desk as a thinclient, but I want to basically be using the other machine, which has a nice Kubuntu install, plenty of RAM and processing power, plus all my data.

My idea is this: install a minimal Ubuntu on the Compaq "thinclient", and then have a KDM login screen come up that logs me into the "Media Server". Should I use FreeNX for this (I've heard that the packages are having issues, and the nocomputer site is down) or should I use basic X11 forwarding? Everything is on a 10/100 internal LAN.

Oh, and I would have a USB printer and speakers hooked up to the "thinclient", which would need to be functional. Printing is easy (setup cups on the thinclient, and then add that printer to the server's list of printers - I can do that within KDE). But how do I tell the server to forward sound over to the thinclient's speakers when I have a session open from the thinclient? I'm currently using aRts, with ALSA as the backend.


Any help is most appreciated. If I get it working, it will make a sweet HowTo!

---

### Post by az on 2005-05-17
[http://packages.ubuntu.com/hoary/net/ltsp-utils](http://packages.ubuntu.com/hoary/net/ltsp-utils)

You want: Linux Terminal Server Project

---

### Post by kiddyfurby on 2005-05-18
NX would be perfect for you - it even setup printers and sound!!

---

### Post by Locomorto on 2005-05-18
[QUOTE=philipacamaniac]I want to move my main desktop into my living room to act as sort of a "media server". It has a nice functional Kubuntu install, and eventually I'll be adding MythTV and a tuner card.

But, I still need a computer at my computer desk, for email, web surfing, documents, blah blah. I have an extra Compaq 500Mhz Celeron machine. I want to use it at the computer desk as a thinclient, but I want to basically be using the other machine, which has a nice Kubuntu install, plenty of RAM and processing power, plus all my data.

My idea is this: install a minimal Ubuntu on the Compaq "thinclient", and then have a KDM login screen come up that logs me into the "Media Server". Should I use FreeNX for this (I've heard that the packages are having issues, and the nocomputer site is down) or should I use basic X11 forwarding? Everything is on a 10/100 internal LAN.

Oh, and I would have a USB printer and speakers hooked up to the "thinclient", which would need to be functional. Printing is easy (setup cups on the thinclient, and then add that printer to the server's list of printers - I can do that within KDE). But how do I tell the server to forward sound over to the thinclient's speakers when I have a session open from the thinclient? I'm currently using aRts, with ALSA as the backend.


Any help is most appreciated. If I get it working, it will make a sweet HowTo![/QUOTE]
 Just so you know, breezy is set to get thinclient support, or atleast it is a goal. So if you cannot get it working now, breezy should have it eventually.

---

### Post by philipacamaniac on 2005-05-18
[QUOTE=azz][http://packages.ubuntu.com/hoary/net/ltsp-utils](http://packages.ubuntu.com/hoary/net/ltsp-utils)

You want: Linux Terminal Server Project[/QUOTE]

I've looked at LTSP, and it is entirely too complicated. Plus, it loads a kernel through the network, but I have a hard disk on my "thinclient" and want a barebones Ubuntu install available on it.
EDIT: I've also heard that FreeNX runs speed circles around LTSP. But I will take another look at it anyway.

Locomorto, I'll try that when Breezy is a little closer to release. Thanks!

Kiddyfurby, I installed the freenx stuff on the server, but haven't tried the client bit yet. I only need an X server on the client, right? I don't need KDE or even a local window manager at all, do I? Do you know if FreeNX brings up a KDM/GDM screen, or does it have its own login prompt?

---

### Post by kiddyfurby on 2005-05-19
you will need nxclient on the thin client
to make things simple (though not as secure)
you can select Nomachine key during install

NX let you login a new session, unlike vnc, you are not controlling the server desktop
you can select KDE / GNOME in the client, username and password goes to the client as well

---

