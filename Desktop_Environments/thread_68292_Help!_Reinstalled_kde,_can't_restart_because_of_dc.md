---
title: "Help! Reinstalled kde, can't restart because of dcopserver"
date: 2005-09-22
forum: Desktop Environments
---

### Post by reuben on 2005-09-22
Hello, 

I was attempting to do an upgrade in synaptic, but it was blocked due to broken packages. The broken package was libqt3c102-mt, which was at 3.3.3.4, a non-ubuntu version. I tried to back it up a couple versions, but it would only uninstall, and part of the uninstall would take the entire kde app with it. I figured this was worth doing to get apt happy again, and so removed kde (and all dependencies.)

I reinstalled by doing: 
sudo apt-get install kdebase

Then tried:
startx

Two things happen;
1) I get a dialog which flashes up real quick complaining about dcopserver not being started
2) Then kde initialization freezes on "Initializing Interprocess Communication"

So, I drop back to the shell, kill X, start dcopserver, and run startx again. It gets to "Initializing Interprocess Communications", does something for about a minute, and then crashes. On the shell are a ton of error messages from Dcopserver; unfortunately I didn't write them down, but they had to do with iceauthority connection or protocol not being allowed.

I'm now operating within fluxbox, which kind of sucks. 

BTW, I did install Opera a couple of days ago (the static deb); is it possible that that caused the apt brokenness?

---

### Post by reuben on 2005-09-22
Solved. Removed everything, reinstalled kde-core. Now it works.

---

