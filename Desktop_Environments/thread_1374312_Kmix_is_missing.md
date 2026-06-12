---
title: "Kmix is missing"
date: 2010-01-06
forum: Desktop Environments
---

### Post by Falc7 on 2010-01-06
Title says it all ready, i have tried removing kmix package completely, then reinstalling, but its still missing from the notification area.

---

### Post by Zorael on 2010-01-07
Is it running? :3 (Alt+F2, 'kmix')

I've gotten a bug where it sometimes doesn't start after logging in. I ended up writing an autostarted script that started it if needed (and otherwise did nothing), but that was a few releases back.

---

### Post by Falc7 on 2010-01-07
It seems you are right, kmix isen't starting, even though i've added it to the auto start list in system settings, i am guessing the auto start list is pretty buggy then?

---

### Post by Zorael on 2010-01-07
I'm really not sure, perhaps it could even be starting properly but then crashing (silently).

```
#!/bin/bash
# Script that waits 10 seconds, then starts kmix if it isn't already running

sleep 10

pid=$(pidof kmix)
# Use the below line instead if you're running several users (at the same time)
# pid=$(ps x | grep kmix | grep -v grep)

if [ ! "$pid" ]; then
  # kmix not running, start
  kmix &
  disown %1
fi
```

---

### Post by Falc7 on 2010-01-07
I should save that script in kate, and added it to the autostart scripts in system settings, is that correct?

---

### Post by Zorael on 2010-01-07
Hmm, saving it in **~/.kde/Autostart/** should make it pop up automatically in System Settings -> Autostart. But you can add it via the menus there, too.

Just make sure to set it executable, such as by right-clicking it in Dolphin and going to the Permissions tab and checking that little box. When I tried adding a test script just now, it ended up in the correct directory but without being set executable. So likely upon logging in, it would be opened up in Kate (like a text file) instead of run (as a script).

---

### Post by Falc7 on 2010-01-08
Ok kmix still dosen't start if i do a cold boot. However if i log in, then log out, then log in again kmix starts, abeit in a maximised state, rather than appearing quietly in the notification area.
This is what bootmanager shows, i believe that kmix dies during the process:
[http://img691.imageshack.us/i/jamiekubuntukarmic20100.png/](http://img691.imageshack.us/i/jamiekubuntukarmic20100.png/)

---

### Post by Zorael on 2010-01-08
When kmix is started, it silently places itself in the system tray. If it's started again while in the tray, it pops up as a window. So when you say it shows up in a maximized state (window), that likely means it was started while already running.

The script is supposed to hang back for 10 seconds and *then* check if kmix is running, and if not, start it. The idea is to give kmix a chance to autostart, and if it wants to, crash. Then when the script wakes (after those 10 seconds), it realizes kmix isn't running and starts it.

You could try increasing the delay (fourth line, **sleep 10**) to say, 20 seconds (**sleep 20**), and see if it works better for your machine. Perhaps 10 seconds isn't enough to let kmix start and crash.

I'm unsure how to properly catch if and why kmix could be crashing during boot. If it does, it's supposed to spawn the bug reporting tool, DrKonqi.

---

### Post by Falc7 on 2010-01-08
Well if i log in first time, kmix isen't in the system tray, and if i start it in the terminal it appears silently in the system tray.
And if i log in, then log out, then log in, it appears like it should, and the entering password -> desktop time is also much much shorter. 

Its almost as if when i log in the second time, everything runs perfectly, but the first time everything is slow and kmix fails to start. Could it be related to the fact that i did a server install first then installed kde minimal?

---

### Post by Zorael on 2010-01-08
Well, the second login is bound to be faster, since some stuff is probably already in memory.

Are you sure the script is starting, then? Is it executable, and does it show up in System Settings -> Autostart? It's supposed to work around this.

---

### Post by Falc7 on 2010-01-08
Yep i'm sure:
screenshot
[www.ubuntu-pics.de/bild/37206/screenshot_001_kAzX8A.png](www.ubuntu-pics.de/bild/37206/screenshot_001_kAzX8A.png)

If the worst comes to the worst i'll do a clean install, this, combined with very very long wait from password -> ready desktop, is worth the hassle of a clean install

Edit: I don't really have an explanation, i was playing around, tried removing all traces of kmix from the autostart manu and purging from synaptic, then reinstalling, now it seems to be starting by itself, i'll double check kmix starts reliably now.

---

### Post by Falc7 on 2010-01-09
Hi
The fix before wasent very reliable, so i did a clean install, seems to be working fine now

---

