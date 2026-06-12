---
title: "Icons/clickability gone from desktop."
date: 2006-03-21
forum: Desktop Environments
---

### Post by Ian Maxwell on 2006-03-21
Somehow I managed to kill the icons on my GNOME/Metacity desktop the other day. Clicking (left or right) on the desktop has no effect either. This happened immediately after I tried to kill a misbehaving window, so it's conceivable I did something dumb like kill some desktop process instead. At any rate, the classic "reset the computer" fix didn't seem to work.

I'd appreciate any help I can get figuring this out.

---

### Post by resolutioncenter on 2006-03-21
Nautilus is responsible for the desktop in Gnome, so I think you simply killed nautilus.

Try to restart it, maybe from a terminal to see if you get any error messages if it doesn't start.

Hope this helps.

---

### Post by Ian Maxwell on 2006-03-21
Thank you! All it took was to type "nautilus" at the command line and everything is spiffy again.

---

