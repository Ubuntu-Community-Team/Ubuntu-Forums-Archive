---
title: "How to refresh the background automatically in LXDE/Pcmanfm?"
date: 2012-09-07
forum: Desktop Environments
---

### Post by kataja on 2012-09-07
As in title, how to force refresh of the background image? I have an updating image and I would like to set it as a dynamic background. Currently using Lubuntu 12.04 with LXDE environment and Pcmanfm file manager.

---

### Post by cortman on 2012-09-07
Are you looking for an automatic wallpaper changer?
I've not used it, but I've heard good things about Wallch- available in the Ubuntu repositories.

```
sudo apt-get install wallch
```

EDIT: Wallch may not work with LXDE- you could also try [this script]("http://ubuntuforums.org/showthread.php?t=1843824"), made for LXDE, or Variety, outlined in the last post of that thread.

---

### Post by kataja on 2012-09-07
> **cortman said:**
> Are you looking for an automatic wallpaper changer?
I've not used it, but I've heard good things about Wallch- available in the Ubuntu repositories.

```
sudo apt-get install wallch
```

EDIT: Wallch may not work with LXDE- you could also try [this script]("http://ubuntuforums.org/showthread.php?t=1843824"), made for LXDE, or Variety, outlined in the last post of that thread.

Thanks, the link's script does the trick!
Actually, all I needed was
```
pcmanfm --set-wallpaper=something.jpg --wallpaper-mode=fit
```

I run it as crontab with the script which makes the backgorund itself.  ;)

---

### Post by cortman on 2012-09-07
> **kataja said:**
> Thanks, the link's script does the trick!
Actually, all I needed was
```
pcmanfm --set-wallpaper=something.jpg --wallpaper-mode=fit
```

I run it as crontab with the script which makes the backgorund itself.  ;)

Excellent! Glad it's solved. :)

---

### Post by kataja on 2012-09-08
If somebody reads this topic and has a similar crontab system, remember to add DISPLAY=:0 to the crontab file. The cron can't otherwise open the display and the background won't refresh.

---

### Post by hakermania on 2012-09-08
New versions of Wallch work on LXDE too. You just need to configure your desktop environment at the set custom command dialog. You can install the latest versions of Wallch like this:
```

sudo add-apt-repository ppa:wallch/3+
sudo apt-get update && sudo apt-get install wallch

```

---

