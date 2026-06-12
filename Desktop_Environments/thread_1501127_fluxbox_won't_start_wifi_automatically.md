---
title: "fluxbox won't start wifi automatically"
date: 2010-06-03
forum: Desktop Environments
---

### Post by keraunoscopia on 2010-06-03
I just installed Ubuntu 10.04 onto my Inspiron laptop.  I'm running fluxbox as my display manager.  I'd like fluxbox to start nm-applet and log me into a wireless network automatically on startup, without having to enter the network key or enter my password for a second time.

To that end, I put the line "nm-applet &" in the .fluxbox/startup before fluxbox starts up. If I understand correctly, nm-applet should get the key from gnome-keyring-daemon.  Typing "ps ax" after fluxbox has started confirms that the keyring daemon is running.  However, each time I start fluxbox nm-applet brings up a box asking me to enter the network key.  It seems nm-applet isn't talking to gnome-keyring-daemon.

I tried adding a line in .fluxbox/startup to launch gnome-keyring-daemon before launching nm-applet.  Now the keyring daemon brings up a box asking me for my password, and "ps ax" shows two copies of gnome-keyring daemon running.

Any suggestions on how to get this working would be much appreciated.

Jeff

---

