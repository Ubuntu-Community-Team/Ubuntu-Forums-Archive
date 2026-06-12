---
title: "Is is possible to make a different desktop background for each workspace?"
date: 2009-03-31
forum: Desktop Environments
---

### Post by camper365 on 2009-03-31
I use the Desktop Cube, and I was wondering if it was possible to make each desktop have a different background?

---

### Post by _Purple_ on 2009-03-31
Check [this](http://ubuntuforums.org/showthread.php?t=69507&highlight=different+background+workspaces) thread.

---

### Post by UbuntuNerd on 2009-03-31
you can also check [here](http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10)

---

### Post by lordbah on 2009-04-01
> **UbuntuNerd said:**
> you can also check [here](http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10)

Wow, that page is unreadable. Dark gray text on black background.

---

### Post by drs305 on 2009-04-01
I used Wallpapoz before compiz and it worked fairly well. Wallpapoz could do the job but compiz is now much easier, using the CompizConfig Settings Manager as linked previously. Unfortunately I think you still lose the Desktop with compiz.

One thing you will have to do to get a different wallpaper to display on each workspace is to turn off compiz's "show_desktop". If you don't, you will have different wallpapers until you open nautilus, then you may lose them. This has been reported as a bug, but as of Jaunty beta, I still lose my wallpapers if I don't turn the desktop off in gconf.

You can either open gconf-editor as a user and as root and go to the apps/nautilus/preferences section, or run these two commands:
```

gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'false'
sudo gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'false'

```

---

### Post by camper365 on 2009-05-03
The problem is that if I do that, I don't have the icons on my Desktop anymore.

---

### Post by UbuntuNerd on 2009-05-03
you can still see what's on your desktop by clicking on Places > Desktop also somebody came up with this work around but I have not try it:  
[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

---

### Post by camper365 on 2009-05-27
It looks like that work-around only works with pre-Hardy. I don't want to downgrade to an unsupported version to get icons on my desktop and multiple backgrounds (I know Dapper is still technically supported, but its EOL is close).

---

### Post by deadlockedgamer on 2009-05-28
if you go to ubuntu brainstorm page and go to ideas in development you will see this is being worked on. You can even see the developers comment. It is being worked on to try and get it in 9.10

---

