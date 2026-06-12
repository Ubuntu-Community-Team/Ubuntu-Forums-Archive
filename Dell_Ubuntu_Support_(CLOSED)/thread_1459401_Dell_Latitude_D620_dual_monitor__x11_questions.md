---
title: "Dell Latitude D620 dual monitor / x11 questions"
date: 2010-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epoh on 2010-04-21
Ok, y'all are going to laugh at me, but I am tired and cannot figure this out. 

My setup - 
Dell Latitude D620
Ubuntu 9.10
laptop video - Intel Mobile 945GM
monitor - Dell 19" LCD (do not know the model off-hand)

The display works fine on just my laptop. And also with the laptop and monitor mirrored. When I try to unmirror and configure both monitors as they should be (laptop 1440x900, monitor 1280x1024) both my screens go black and I've had to reboot to get the display back (I forgot about doing ctrl-alt-f1, to be honest, to recover.)

1) I cannot find a xorg.conf file anywhere. Where should I be looking?

2) Do I need to download/configure any 3rd party apps to make my dual-monitor setup function properly. 

Shockingly enough, I am a RedHat server admin, but I have no experience with Ubuntu. I do not mind hacking away at it from the command-line, I'm just at a loss as to where X11 is getting it's config from right now.

---

### Post by epoh on 2010-04-22
Nothing?

---

### Post by epoh on 2010-04-22
Well, I've (sort-of) fixed my own problem. I had to disable Visual Effects to get the second monitor to work. (boo)

Secondly, apparently in 9.10 there's no longer an xorg.conf included by default. good to know.

---

### Post by epoh on 2010-04-26
If anyone cares, the issue is completely resolved in 10.04.

---

