---
title: "how do i change default video viewer in any browser"
date: 2006-05-31
forum: Desktop Environments
---

### Post by blastradius on 2006-05-31
Hi

I'm using Firefox (1.5.0.3), I've also tried Galeon and Mozilla.  I'm trying to view streaming video (actually from the BBC cricket site).  The error i get is :-

'could not find an appropriate hxplay or realplay in the system path to use as an embedded player'

I have realplayer installed as well as Totem and mplayer so I'm guessing the browser can't find them, question is, how do i put it right??

I'm using Ubuntu Breezy.

Thanks in advance

Eric

---

### Post by johnc4510 on 2006-05-31
flashplugin-nonfree
this should be in synaptic if you have enabled universe and mutiverse

sudo apt-get install flashplayer-nonfree
sudo /usr/sbin/update-flashplugin

---

### Post by johnc4510 on 2006-05-31
Sorry, that's not right. That's for flash not streaming video. Try this:
sudo apt-get install totem-gstreamer-firefox-plugin

---

