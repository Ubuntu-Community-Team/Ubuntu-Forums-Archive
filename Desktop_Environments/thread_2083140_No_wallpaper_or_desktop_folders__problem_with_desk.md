---
title: "No wallpaper or desktop folders / problem with desktop environment?"
date: 2012-11-11
forum: Desktop Environments
---

### Post by Treyonator56 on 2012-11-11
Hey Everyone. I recently upgraded from Lubuntu 12.04, to Lubuntu 12.10. It appears everything went fine, except I have no wallpaper or folders on my desktop anymore. I've searched on these forums, and other forums, with no such luck on the answer I need. I was going to switch to Ubuntu, to see if that fixed my problems, but I'd have to mount my music folder to a different partition, and download the .iso, but that would take way too long, since I'm tethering internet through my Android. Anyways, does anyone know how to fix this? I've looked around, and I couldn't find any answers.

[Desktop]("http://i50.tinypic.com/30wru69.png")

[Desktop Folders]("http://i47.tinypic.com/1jkaav.png")

Note: Nothing has been edited or changed.

---

### Post by critin on 2012-11-12
Have you run the updates yet?  You're aware that 12.04 is the stable LTS version, while 12.10 is still buggy, so these things will happen.  

Also, have you checked Additional Drivers?

---

### Post by Treyonator56 on 2012-11-12
12.04 isn't LTS for Lubuntu, and I haven't checked for additional drivers yet. I'll try that when I get home.

---

### Post by Treyonator56 on 2012-11-12
I checked for additional drivers, and no proprietary drivers are in use. I updated everything also, and my desktop is still gone. Thanks for trying to help though, critin.

---

### Post by ankspo71 on 2012-11-16
Hi,
pcmanfm is the application that displays the desktop in Lubuntu, so maybe it is not loading properly on startup.

Try opening a terminal and pasting this command:
```
pcmanfm --desktop --profile lubuntu
```

If that fixes the desktop, then you will need to find out why is is not working on startup, so check the contents of this file:
```
cat /etc/xdg/lxsession/Lubuntu/autostart
```

It should look like this:
> @lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu

It might be a problem with pcmanfm's configuration files too.

---

