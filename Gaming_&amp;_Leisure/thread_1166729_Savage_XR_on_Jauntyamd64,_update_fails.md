---
title: "Savage XR on Jaunty/amd64, update fails"
date: 2009-05-22
forum: Gaming &amp; Leisure
---

### Post by shazbut on 2009-05-22
Like the title says.  I've built a new box and installed 9.04 64bit version on it.  Installed Savage XR from newerth.com fine, but when I launch it i get:
```
ERROR: Failed to contact update server!

Please check your internet connection and firewall and restart the application to get the latest updates.

Would you like to launch the application anyway?
```
Tested on the old box (8.04/32bit) and is still updating there, so it's not the update servers.  Does anyone know why it would fail under 64bit version.  The game does install some common libraries in its own folder.

Also, downloads of custom maps fail when I connect to a server in the game.  Connecting to servers with the standard maps is ok.

ps: I'd post this under the 64 bit request thread but it appears I'm not allowed to submit replies for some reason.

---

### Post by shazbut on 2009-05-26
I'll answer my own post here.  As per the recent discussion over on the [Newerth forums]("http://http://www.newerth.com/smf/index.php/topic,6616.30.html") Ubuntu does not install the lib32nss-mdns library when you install ia32-libs.  So all you need to do is:
```
sudo apt-get install lib32nss-mdns
```
and updates should start working again.
Hope this saves someone some time.

---

