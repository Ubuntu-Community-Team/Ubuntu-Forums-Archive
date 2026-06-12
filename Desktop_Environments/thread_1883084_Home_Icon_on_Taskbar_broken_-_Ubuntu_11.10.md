---
title: "Home Icon on Taskbar broken - Ubuntu 11.10"
date: 2011-11-18
forum: Desktop Environments
---

### Post by servventer on 2011-11-18
When I click on the "Home" folder icon another "Shell" icon appears on the taskbar. See attachment. This also has "Home" tag but if I close this icon the original "Home" icon becomes unusable. I have reset my Unity icons, restarted Unity to no avail. I have now removed the Home icon and open the the folder from the Dash.

---

### Post by jerrrys on 2011-11-19
you could also drag and drop "File" to the launcher panel and have home access.

or you could reinstall the "launcher-panel"

---

### Post by stinkeye on 2011-11-19
In the terminal....
```
gedit ~/.local/share/applications/nautilus-home.desktop
```


and comment out the line 
```
OnlyShowIn=GNOME;Unity;
```

ie put a hash in front
```
[COLOR="Red"]#[/COLOR]OnlyShowIn=GNOME;Unity;
```

---

