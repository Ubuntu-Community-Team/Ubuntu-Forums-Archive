---
title: "Run bash display script after logon for correct resolution"
date: 2014-11-22
forum: Desktop Environments
---

### Post by stretch3 on 2014-11-22
I am having issues with the display on my old Dell Dimension 3100 which has Intel integrated graphics, running Lubuntu 14.04. On startup, it defaults to 1024x768 where the native screen resolution is 1280x1024. I can get it back to 1280x1024 following the link below but I have to do it on each boot which is annoying.

[http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution](http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution)

I made this script which sets the correct resolution which works if I run it manually once logged into the desktop environment. I tried to set it up in crontab so the script runs on each reboot (i.e. "@reboot sh path/to/script.sh") but that didn't work. Any ideas how to make this script run once in the desktop environment?

```
#!/bin/bash
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 "1280x1024_60.00"
xrandr --output VGA1 --mode "1280x1024_60.00"
```

---

### Post by agillator on 2014-11-22
You should be able to set your display resolution through the settings manager so you don't have to use a script. However, if that doesn't work and/or you want to use a script anyway, put the script in /etc/init.d and then put links to it in the various /etc/rcX.d directories or start the script from the rc.local script.

---

### Post by stretch3 on 2014-11-29
I found a quick way to automatically set the correct resolution with xrandr at this link under **Setting xrandr changes persistently**

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

So to run the xrandr commands at logon, I created a new file:

```
nano ~/.xprofile
```

paste and save the following in the file

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 "1280x1024_60.00"
xrandr --output VGA1 --mode "1280x1024_60.00"
```

and it works fine on a per user basis as explained in the article linked :cool:

---

