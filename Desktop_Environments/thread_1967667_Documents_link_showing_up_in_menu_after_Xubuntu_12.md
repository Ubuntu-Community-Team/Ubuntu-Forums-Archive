---
title: "Documents link showing up in menu after Xubuntu 12.04 upgrade"
date: 2012-04-28
forum: Desktop Environments
---

### Post by ccrs8 on 2012-04-28
The upgrade from Xubuntu 11.10 to 12.04 went very smoothly.  No surprises or gotchas to be had.  However, there is one very strange thing that I can't figure out.  In my main menu, there is now a "Documents" link right between "Accessories" and "Games."  There is no expansion arrow next to it, and all it does is open up my home/myusername/documents folder in Firefox.

I'm trying to get rid of it, but I can't figure out how.  It does not show up in Alacarte when I right click on the main menu button, go to properties, and go to Edit Menu.  I can't find it anywhere in the configuration files of either /etc/xdm/menus or home/myusername/.config/menus.

This did not happen when I upgraded my laptop to Xubuntu 12.04 yesterday, and my laptop and this desktop's main menu were configured the same way.  Very strange.

Any idea what is going on and how to remove it?  I've attached a screenshot for reference.

---

### Post by ccrs8 on 2012-04-28
I ended up just copying all the .menu files from the working laptop to the desktop, and that cleared up the issue.  It looks like the problem was cleared up once I replaced the files in my home .config/menu directory.  I compared the two files and could not see what the difference was, so I still don't know what was going on.

---

### Post by ccrs8 on 2012-04-28
OK, now I see what the problem was.  The offending section of the ~/.config/menus/xfce-applications.menu file was this, at the top level:

```
<Include>
		<Filename>alacarte-made.desktop</Filename>
</Include>
```

---

