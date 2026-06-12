---
title: "OpenBox and wireless problem"
date: 2010-03-07
forum: Desktop Environments
---

### Post by brandon88tube on 2010-03-07
I can't figure out how to start up my wireless when I run just an OpenBox session. Any help to get this up and running would be greatly appreciated.

---

### Post by nothingspecial on 2010-03-07
Try wicd.

It starts at boot.

---

### Post by hhh on 2010-03-07
You didn't say how you were running Openbox, or whether you had a working wireless connection with another configuration, but I can tell you what works for me. I have a standard Karmic setup, wireless works with Network Manager. I added a stand-alone Openbox session to that, added the following to Openbox's autostart.sh file...
```
nm-applet &
```
Network Manager now connects automatically when I login to my Openbox session, same as with my Gnome session.

---

### Post by brandon88tube on 2010-03-07
I'm trying to run an OpenBox session by itself. I originally had a gnome install that has a working wireless that is using NetworkManager and the nm-applet. If I didn't originally have this setup how would I go about connecting wirelessly? I'm curious because I might try to do a clean install sometime in the future with just OpenBox.

---

### Post by eriqjaffe on 2010-03-07
If you're going from a blank slate with just Openbox, I highly recommend you use wicd - it'd be easier if you have a wired connection so you can just apt-get it.

Wicd will run as a daemon - if you want to have a tray icon, you can add 
wicd-client &" to your autostart.sh file.

---

### Post by brandon88tube on 2010-03-08
Hmm, for the time being seeing as how its already installed for now, I've been running nm-applet. Is this a gnome app? Either way, I guess I'll have to try out wicd one of these days.

---

### Post by eriqjaffe on 2010-03-08
Yeah, nm-applet is a Gnome app, which is why you already have it available.

---

### Post by brandon88tube on 2010-03-10
Just an update if anyone was interested. I've been using wicd for a little bit now and it seems to be ok. Can't really compare except that it runs way before nm-applet ever would. Think it runs right after boot when its loading daemons etc.

---

