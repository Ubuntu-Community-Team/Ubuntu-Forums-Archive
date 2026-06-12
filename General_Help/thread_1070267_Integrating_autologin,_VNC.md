---
title: "Integrating autologin, VNC ?"
date: 2009-02-15
forum: General Help
---

### Post by gurlinux on 2009-02-15
Hi,

I am setting up a Xubuntu server at home, which will act as a file server and torrents downloader. I want it to automatically start all services and applications, as it will be a headless (no-monitor) server accessible via VNC.

So far, for torrents I am using uTorrent under wine, that's working fine just like VNC, but the problem I am finding is that if I configure autologin for the user which will autostart uTorrent, then when I manually VNC from another computer I get a completely new "user environment", even if I login using the same ID as the autostarted one.

So the thing is I can't see the 'real' autostarted user, where my uTorrent window is.

What am I doing wrong? How can I set this up so I can see the autologged-in user environment? Or, should I use another (linux-native) torrent client that allows better integration? I'm just using uTorrent because I like its flexibility, but I'm open to all suggestions...

Thanks a bunch!
[I]
Disclaimer: I'm quite a noobie... of course...[/I]

---

### Post by composites on 2009-02-22
I think VNC will open a new server :1 instead of your native one :0. I was having the same problem as you, but partly solved it using [this guide](http://ubuntuforums.org/archive/index.php/t-279069.html). Now I am able to view the native server (in your case the one running uTorrent), but am unable to input anything with the mouse or keyboard. If this helps at all I'd be interested to know.

---

### Post by gurlinux on 2009-05-14
For the record, and posterity, here's what I found:

I was using TightVNC server for providing the VNC service at the Xubuntu machine. After much frustration and endless testing, I was tipped of **THE **great enlightening knowledge: **TightVNC server always opens a new session**. It cannot do what I want.

The same tip (and a few more) suggested to use x11vnc instead.

[This thread]("http://ubuntuforums.org/showthread.php?t=944187") explains how to configure x11vnc exactly for this purpose. *Happy VNCing!*

I still have to find the time to actually do it, but I'll report the results then.

---

