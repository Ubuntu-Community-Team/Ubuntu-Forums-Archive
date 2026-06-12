---
title: "Broken Dependancies/ Trevino's Repo's"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by RandomUsr on 2007-08-18
After attempting to update to compiz fuzion 0.5.x I now have broken dependancies. I don't believe there is an uninstaller, so what can I do To resolve this issue?   I can post the output from the commands if it helps.

Also, I'm not able to manually edit and systemwide config files, such as etc/apt/sources.list or xorg.conf 

I always get an error stating that I'm not the owner of the file. Will chmod work?

---

### Post by FuturePilot on 2007-08-18
Open Synaptic and use the Fix Broken Packages feature. It's in one of the menus.
As for editing the files you need to use sudo or gksudo
Example:```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by luisromangz on 2007-08-18
Well, to use Treviño's repository you should have activated the universe and multiverse repositories first. Maybe that solves the dependency problems.

To edit systemwide config files, your user needs to gain root privileges, so use sudo (or one graphical equivalent, as gksudo or kdesudo) before the command you were triying to edit the file. You can edit /etc/apt/sources.list from Synaptic itself.

---

