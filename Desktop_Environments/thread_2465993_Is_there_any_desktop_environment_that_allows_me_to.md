---
title: "Is there any desktop environment that allows me to rename running apps?"
date: 2021-08-17
forum: Desktop Environments
---

### Post by kwanbis on 2021-08-17
At work, I run 6 projects. 

I want to have one Chrome/Firefox window per project, and in each window have x number of tabs that belong to each project.

I can do that just fine with Chrome/Firefox. However, I want each window icon, to have the name of the project.

Normally, Chrome/Firefox will show the name of the current TAB instead.

I can do that in Windows using an app called TaskBar Renamer [https://kwaschny.net/projects/taskbar-renamer](https://kwaschny.net/projects/taskbar-renamer)

Is this possible with Ubuntu somehow? Thanks!

---

### Post by &amp;KyT$0P# on 2021-08-17
There are desktop-environment-independent ways to do this.  You could try something involving wmctrl.  Or use a Firefox/Chrome extension or Violentmonkey user script.

---

### Post by TheFu on 2021-08-17
Perhaps using TreeStyleTabs addons in the browser will let you organize the tabs better?  Those in the same project can be sub-tabs, for example.  The title for the page is what the tab will have, so if the title is the project name, you should be good, automatically.

TreeStyleTabs does get confused and I think it leaks memory, so restarting weekly is needed.  It can be toggled off and on with an icon and that fixes most of the issues I see.  Once you have TreeStyleTabs, you'll wonder why horizontal tabs are even used anywhere still.

---

### Post by kwanbis on 2021-08-18
> **TheFu said:**
> Perhaps using TreeStyleTabs addons in the browser will let you organize the tabs better?  Those in the same project can be sub-tabs, for example.  The title for the page is what the tab will have, so if the title is the project name, you should be good, automatically.
Thanks. I tried it but it is not exactly what I want. Much closer is Tab Outliner. But it is not exactly as needed.

---

### Post by kwanbis on 2021-08-18
> **halogen2 said:**
> There are desktop-environment-independent ways to do this.  You could try something involving wmctrl.  Or use a Firefox/Chrome extension or Violentmonkey user script.
Thanks. I tried many extensions and none does what I want. Maybe I could try violentmonkey.

---

### Post by vanadium on 2021-08-18
It could be done with different profiles, which you then can start up assigning a different WM_CLASS.

```
firefox -P project1 --class project1
```

would start up firefox with a specific profile and a specific WM_CLASS. The icon will be separated from a "normal" Firefox instance on the Alt+Tab application switcher or from a dock because of the different class. A different name and icon can be specified in a dedicated .desktop launcher.

---

### Post by TheFu on 2021-08-18
> **kwanbis said:**
> Thanks. I tried it but it is not exactly what I want. Much closer is Tab Outliner. But it is not exactly as needed.

You can rename a title for a window using **wmctrl -T {name}** provided the WM is compliant with standards.  I fear that Gnome3+ is not.  Also, I don't know if this works with Wayland or not.  It has worked for decades under X/Windows, however. Most old-school programs support the standard X/Windows options which control the window decorations.  FYI, the WM, Window Manager, is responsible for everything around an application - the border, thickness, color, size of the window, any buttons and which signals those buttons send into the application.
I have an image here with this already .... 
[ATTACH=CONFIG]289000[/ATTACH]
See the window border and 2 buttons in the upper right-hand corner?  That's controlled by the WM, not the application. The gray color is for a window that isn't active. That's also configurable by the WM. On my systems, the active window is cornflower blue.

The hard part of using wmctrl is getting the windowID, since all commands work using that. **wmctrl -l** provides a list with the current titles and state (open, desktop, iconified, etc)
```
$ wmctrl -l |egrep Firefox
0x03800003  0 hadar [other] Is there any desktop environment that allows me to rename running apps? - Reply to Topic — Mozilla Firefox

```
So to change the title of 0x03800003, I'd use ```
wmctrl -T "new name" -r 0x03800003
```
That's the theory.

---

