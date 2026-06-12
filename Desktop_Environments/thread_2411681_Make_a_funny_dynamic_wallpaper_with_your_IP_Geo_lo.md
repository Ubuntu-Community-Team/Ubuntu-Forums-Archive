---
title: "Make a funny dynamic wallpaper with your IP Geo located"
date: 2019-02-02
forum: Desktop Environments
---

### Post by xjulie on 2019-02-02
Hi everybody,

Just want to share with you a tip to have a nice dynamic wallpaper that  displays your IP address on the planet earth with realtime sun light  (day and night).

[IMG]https://xj1.fr/tmp/earth_screenshot.jpg[/IMG]

You can preview the wallpaper with your IP (1920x1080) here : [https://checkip.ninja/ip-earth.php](https://checkip.ninja/ip-earth.php)

On ubuntu 18.04 with gnome, simply download it with a crontab like this : 

```
* * * * * wget -O /home/user/Pictures/earth.jpg https://api.checkip.ninja/earth.jpg

```

and set earth.jpg as your wallpaper. I find it particularly useful when I  use a VPN, which allows to visualize immediately where is my IP.  Incidentally, I find it pretty!

---

