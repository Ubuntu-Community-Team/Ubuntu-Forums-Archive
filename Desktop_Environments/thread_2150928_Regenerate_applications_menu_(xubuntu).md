---
title: "Regenerate applications menu (xubuntu)"
date: 2013-06-02
forum: Desktop Environments
---

### Post by Svictor on 2013-06-02
After some messing around with my config files, it seems I have accidentally deleted the applications menu file, and the xfce4-settings-manager menu file. My /etc/xdg/xdg-xubuntu/menus/ is empty, and so is /etc/xdg/menus/
I expected to regenerate them with update-menus but this doesn't work.
I also tried to install and remove one of the programs with an entry in the menu, hoping that it would regenerate the whole thing. But this doesn't work neither. 
Then I tried to purge/reinstall xfce4 and xfdesktop, but no luck.

So question is: is there a specific xubuntu command to regenerate the menus? Alternatively which package can I reinstall to replace the deleted menu files?

---

### Post by dentaku65 on 2013-06-03
Try to see if the .menu file is saved somewhere
```
sudo updatedb
locate xfce-applications.menu
```
In my case I have it here:
> /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu
$HOME/.config/menus/xfce-applications.menu

---

### Post by Svictor on 2013-06-03
Thanks! That could have worked... But my menu file was really gone, in both locations. 
However, I just found how to reinstall the default menu. It's in xubuntu-default-settings, so:
```

sudo apt-get remove --purge xubuntu-default-settings
sudo apt-get install xubuntu-default-settings

```
I still haven't understood the actual mechanism for regenerating the menus (why update-menus did not work). But I'll mark the thread as solved. Thanks again!

---

