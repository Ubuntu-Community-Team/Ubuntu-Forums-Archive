---
title: "How do you enable XScreenSaver by default in Xubuntu?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by ZephyrXero on 2006-06-17
I'd really like to have XScreenSaver enabled by default on my laptop running Xubuntu (***XFCE, not Gnome!***), but I can't figure out the proper place for setting this up. Whenever I go into Screensaver settings it informs me that the xscreensaver daemon is not running, and asks me if i'd like to enable it. I've attempted saving my session in hopes that it would still be enabled the next time I booted up, but it didn't work. Do I need to add a command to some startup script somewhere or what?

---

### Post by 23meg on 2006-06-17
Just run the daemon on startup by adding it to your GNOME startup programs as "xscreensaver -no-splash".

I wrote [a guide]("http://ubuntuforums.org/showthread.php?t=195557") on replacing gnome-screensaver with xscreensaver that you can check out. I'll soon post another for just adjusting settings for gnome-screensaver via xscreensaver without completely replacing it.

---

### Post by ZephyrXero on 2006-06-19
I'm talking about for XFCE, not Gnome ;)

---

### Post by ZephyrXero on 2006-06-20
*bump*

---

### Post by ayoli on 2006-06-20
there's must be a y to add startup programms to xfce, btw if you cant find it, you can add this line to your /etc/init.d/rc.local:
```

exec xscreensaver --no-splash
```

---

### Post by mcpish on 2006-06-20
I run XFCE also

1.  Applications > Settings > Autostarted Applications > Add
2.  In "name" enter "xscreensaver" without quotes
3.  In "command" enter "xscreensaver -no-splash" without quotes

---

### Post by ZephyrXero on 2006-06-22
#-o  Well, crap.... I didn't even see that one I guess because it didn't have an icon...doh!

Thanks guys ;)

---

