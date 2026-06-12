---
title: "Xfce Print Screen"
date: 2006-12-31
forum: Desktop Environments
---

### Post by Pobega on 2006-12-31
I'm trying to set Xfce to automatically run the command *gksudo import -delay 3 -window root /var/www/screenshot.jpeg* when I hit Insert, but for some reason it isn't working. Import in general doesn't work, actually (Even import -window root /home/pobega/screenshot.jpeg). 

Help from an Xfce master would be much appreciated!

---

### Post by taurus on 2006-12-31
When you run that command from a terminal, do you get any error message?

---

### Post by Pobega on 2006-12-31
Hm, gksudo didn't seem to work but sudo did. But sudo still isn't suitable for my /var/ww folder, and I don't want to compromise it's safety by changing the permissions.

Is there any way I can make it run say, a bash script, that will open a termina window and run the command? Because using just the command doesn't seem to work (Since it's a sudo-only folder)

---

### Post by maxamillion on 2006-12-31
It sounds like you want to take a screenshot.

```
sudo aptitude install scrot
man scrot
```

enjoy.

---

### Post by Pobega on 2006-12-31
I want it to automatically save to my Apache2 folder, and for some reason no matter what I do it refuses to save into my Apache2 folder. And yes, I'm using scrot now, it's much simpler and easier to understand.

I have Insert tied to *scrot /var/www/screenshot.jpeg*. When I hit insert it does nothing. Whether sudo, gksudo, or none. When I do *scrot /home/pobega/screenshot.jpeg* it brings up a password entering screen, so it seems that it works in /home but not /var. Are there any workarounds for this?

---

### Post by Pobega on 2007-01-01
Bump, I need some ideas. It works somewhat (Will save in /var/www) but I'm trying to get it to save in a folder I made (/var/www/PhotoAlbum) since it includes a PHP Script that automatically sorts my screenshots by date and type.

And linking people to it would be extremely easy with Gaim's text replacement plugin.

---

