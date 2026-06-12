---
title: "Desktop Environment resetting"
date: 2018-02-12
forum: Desktop Environments
---

### Post by piense on 2018-02-12
Twice now my desktop environment has completely reset and still isn't quite right. I'm on 17.10. Yesterday my laptop crashed and when it came back up all sorts of things were wrong. The trackpad was completely broken, couldn't move left or right. Plugged in a mouse and realized the desktop environment was bonkers too. No icons on the desktop, dock was back to default items and items in the file explorer all have a blank icon. I gave up trying to figure it out and just nuked the partition and started over. I grabbed the 17.10 install image and told it to format and do a clean install. Got everything up and running and now it's just done it again, though the trackpad is at least working still, yay! Though tap to click is turned off for some reason. I'm on a late 2011 macbook pro. Pretty much all I'm using is Chrome and Eclipse. Chrome is working still but Eclipse is crashing with "org.eclipse.swt.SWTError: No more handles"  Any help or ideas in figuring out what's going on would be much appreciated!

---

### Post by piense on 2018-02-12
Figured it out, I added another library path to the system and apparently some things conflicted. It was just a bit of a delayed cause and affect which really threw me.

---

