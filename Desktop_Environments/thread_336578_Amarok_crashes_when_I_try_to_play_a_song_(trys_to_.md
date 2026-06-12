---
title: "Amarok crashes when I try to play a song (trys to launch kmail)"
date: 2007-01-11
forum: Desktop Environments
---

### Post by robgill on 2007-01-11
I've been using amarok under gnome for a while now and have no problems, but now whenever I try to play a song it crashes and says "Could not launch the mail client" etc - see screenshot.  It worked fine yesterday, but now even after restarting, I still get this error.

---

### Post by 3ntity on 2007-03-25
> **robgill said:**
> I've been using amarok under gnome for a while now and have no problems, but now whenever I try to play a song it crashes and says "Could not launch the mail client" etc - see screenshot.  It worked fine yesterday, but now even after restarting, I still get this error.

I'm having the same problem... Amarok 1.4.3 under Dapper...

Great music collection, by the way!

---

### Post by PCalitrack on 2007-03-25
Well, I think the mail error is coming because you are running an unrecognized mail program if any. Amarok is for KDE, so I believe it is expecting to run Kontact. It is trying to open your mail program to send a debug report to the developers. My amarok crashes every so often when it can't recognize my playback device. This happens when my soundcard has been unproperly initialized. After a reboot, or sometimes after running booting amarok from the command line, it starts working correctly. I'm am not sure of the semantics behind this though.

---

