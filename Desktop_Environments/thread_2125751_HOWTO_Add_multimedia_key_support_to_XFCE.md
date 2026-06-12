---
title: "HOWTO: Add multimedia key support to XFCE"
date: 2013-03-14
forum: Desktop Environments
---

### Post by Emblem Parade on 2013-03-14
Annoyed that you can't use your keyboard multimedia keys (play, pause, previous, next) in XFCE/Xubuntu?

Here's an easy solution. Actually, this method will let you use any key combination as if it were a multimedia key, so if you prefer SUPER+P for "pause," that will work, too. Yay!

This works for any application that supports "GNOME Multimedia Keys." In effect, it emulates the GNOME interface without actually having GNOME.

1. Download [mkd.py]("http://code.google.com/p/mediakeys-daemon/downloads/list").

2. Make it executable. (chmod +x mkd.py)

3. Settings Manager -> Session and Startup -> Application Autostart. Add a new item and call it "MediaKeys Daemon". The command should be the full path to mkd.py plus the "-d" switch. In my case, it looked like this: "/Depot/Scripts/mkd.py -d".

4. Settings Manager -> Keyboard -> Application Shortcuts. Let's add a shortcut for the "pause" key. The command is again the full path, but this time with the "-a" switch. In my case, it looked like this: "/Depot/Scripts/mkd.py -a". For the key, press the "pause" key on your keyboard (or any other key combination you prefer).

Repeat step #4 for all multimedia keys. Supported switches:

-p Play
-a Pause
-s Stop
-n Next
-p Previous

That's it! Log out, log in again, and the daemon should have been started with your keys properly mapped. Supported application will respond correctly.

---

