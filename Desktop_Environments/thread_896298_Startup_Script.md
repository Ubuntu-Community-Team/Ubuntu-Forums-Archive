---
title: "Startup Script"
date: 2008-08-21
forum: Desktop Environments
---

### Post by ShareBuntu on 2008-08-21
Hi,

I'm running a script 10 minutes after every hour using cron through crontab:

```
#!/bin/bash
wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -nc -O /home/null/sight/wallpaper/world_map.jpg
gconftool-2 --unset /desktop/gnome/background/picture_filename
gconftool-2 --type String --set /desktop/gnome/background/picture_filename "/home/null/sight/wallpaper/world_map.jpg"

```
What I want to do is have the same script execute every time I launch X or GDM so that I have an updated background waiting for me upon login. How would I materialize this unobtrusively - i.e. no delays waiting for it to download before I can use my desktop?

---

### Post by prshah on 2008-08-21
> **ShareBuntu said:**
> 
What I want to do is have the same script execute every time I launch X or GDM so that I have an updated background waiting for me upon login. How would I materialize this unobtrusively - i.e. no delays waiting for it to download before I can use my desktop?

Add the script to your startup sessions (System-Administration (or Preferences?)-Sessions); it will be backgrounded automatically (eg, no need to add "&"). You can also start it up with a modified nice priority (lower priority), by using the "nice" command.

Post back if you want more details.

---

### Post by Loaded.len on 2008-08-21
you could also save your code as /etc/xprofile and make it executable.

Don't know if that will cause the delay you are concerned about, though.

---

### Post by ShareBuntu on 2008-08-21
> **prshah said:**
> Add the script to your startup sessions (System-Administration (or Preferences?)-Sessions); it will be backgrounded automatically (eg, no need to add "&"). You can also start it up with a modified nice priority (lower priority), by using the "nice" command.

Post back if you want more details.
Do I have other options besides "nice"? I presume the command would be "nice /usr/local/bin/wallpaper" - given that wallpaper is executable and exists?

---

### Post by prshah on 2008-08-21
> **ShareBuntu said:**
> Do I have other options besides "nice"? I presume the command would be "nice /usr/local/bin/wallpaper" - given that wallpaper is executable and exists?

Oooer; if you're placing it in /usr/local/bin, ensure that your user can execute it ```
sudo chmod o+x /usr/local/bin/wallpaper
``` I would just place that script in a .scripts/ directory in the home folder... but maybe you're looking at other users on the system using it as well.

The correct format will be```
nice -n 15 /usr/local/bin/wallpaper
``` You can go upto 19 but then it will be very leisurely executed, probably only when the computer goes idle. The default nice "level" is 10, near-realtime -20, and near-idle-time 19. (Yes, the levels are skewed).

---

### Post by ShareBuntu on 2008-08-21
Thanks for the help. It worked perfectly. :)

---

