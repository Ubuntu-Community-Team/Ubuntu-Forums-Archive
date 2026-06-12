---
title: "Cannot get desktop GUI working"
date: 2023-02-14
forum: Desktop Environments
---

### Post by hellmanx on 2023-02-14
I have decided to upgrade from Ubuntu server 18.04 to 22.04 because 18 is near EOL.  I had a Ubuntu Mate desktop environment before the upgrade working as intended.

When the upgrade finished, I was greeted with a blinking underscore.  I was able to figure out how to get to the login prompt and start installing the desktop environment again by doing:

```
[FONT=Consolas]sudo apt update
[/FONT][FONT=Consolas]sudo apt upgrade

[/FONT][FONT=Consolas]sudo apt install ubuntu-desktop

sudo apt install ubuntu-mate-core

sudo apt install lightdm (Set as default)

sudo systemctl start lightdm.service

[/FONT][FONT=Consolas]sudo service lightdm start[/FONT][COLOR=#E8E6E3][FONT=Consolas]

[/FONT][/COLOR]
```

When I reboot / start the OS.  I will see the Ubuntu Mate splash screen and the loading dots.  However, whenever it is done loading.  It will go back to the blinking cursor.
I have also tried slim to see if it would work.  It doesn't.

I'm at a loss for what to do at this point.

---

