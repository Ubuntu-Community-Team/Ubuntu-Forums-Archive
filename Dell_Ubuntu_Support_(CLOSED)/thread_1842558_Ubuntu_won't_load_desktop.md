---
title: "Ubuntu won't load desktop"
date: 2011-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emilward on 2011-09-11
I installed Ubuntu 11.04 on my wife's friend's Dell D400 a few months ago and it works great. But now it won't the desktop. It loads up as normal and when it gets to the desktop I get 3 errors, one after another. The first one says:

"Could not update ICEauthority file /home/bridgette/.ICEauthority"

then it says:

"There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

then it says:
"Nautilus could not create the following required folders: /home/bridgette/desktop,/home/bridgette/.nautilus."

apparently she closed up her laptop will it was in the middle of something. she said there was a message that said it was in the middle of running a script but she didn't know how to stop it and when she turned it back on, this is what she got. I can get to the terminal with no problems (luckily) so I'm assuming that last error message can be fixed by just creating those nautilus folders. However, I'm lost on the first 2. 

anyone that can help???

---

### Post by MG&amp;TL on 2011-09-11
I don't suppose she would remember what script it was running?

---

### Post by MG&amp;TL on 2011-09-11
Ah, This looks VERY similiar.

[http://ubuntuforums.org/showthread.php?t=1841832]("http://ubuntuforums.org/showthread.php?t=1841832")

---

### Post by emilward on 2011-09-12
she said she was online and stepped out and when she came back in there was a popup saying "could not run http:...." where "...." was a string of numbers so it sounds like it was some kind of script that was running while she was online at whatever site she was at. I fixed that last "nautilus" issue by just using:

sudo mkdir

to create those two folders that it could not create. however, I am lost on the first two errors. I read that link you posted and it looks like the issue was never resolved so... I'm up in the air. I hoping I won't have to reinstall ubuntu.

---

### Post by MG&amp;TL on 2011-09-12
I have been going some digging and aparently this works for the .ICE error:

```
sudo chown -R bridgette:bridgette home/bridgette/*
```

Which should allow the system to update ICE.

I'm looking at the other one.

---

### Post by MG&amp;TL on 2011-09-12
Here:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215")

It says that reinstalling gnome panel and changing some permissions should do it...so:

```
sudo apt-get remove gnome-panel
```, then:

```
sudo apt-get install gnome-panel
``` might work.

also:

```
sudo chmod 755 /etc/gconf/gconf.xml.system
``` ?

Sorry I can't help more.

---

