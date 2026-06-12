---
title: "Desktop wallpaper won't change"
date: 2013-04-20
forum: Desktop Environments
---

### Post by neilnoise on 2013-04-20
I recently installed the xubuntu-desktop over Ubuntu 12.10. I'm trying set my wallpaper to change every 5 minutes, but it doesn't seem to be working. In desktop settings, I have it set to image list, and I've ticked "change the background (in minutes) and set it to 5. However it seems to get stuck on the first picture it chooses from the list and doesn't change.

I tried wallch and variety, but even when they said they were working, they weren't overriding the desktop settings so didn't have any effect.

I found this thread [http://ubuntuforums.org/showthread.php?t=2050412](http://ubuntuforums.org/showthread.php?t=2050412) and tried adding this to crontab, but again it didn't do anything.

```
[COLOR=#000000][FONT=Ubuntu Mono]*/5 * * * * DISPLAY=:0.0 xfdesktop --reload > /dev/null 2>&1[/FONT][/COLOR]
```

Any ideas?

---

### Post by neilnoise on 2013-04-20
Update: I tried using shotwell and file -> set as desktop slideshow, but this seems to have affected the lock screen, not the actual desktop!

---

