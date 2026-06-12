---
title: "Remove all shadows Ubuntu 12.04 gnome"
date: 2013-05-17
forum: Desktop Environments
---

### Post by antiserious on 2013-05-17
I'm having an odd, annoying issue and I hope someone here may be able to help. I'm running Ubuntu 12.04 with Gnome, Unity has been removed. I log in with Gnome Classic, no effects, but I still get shadows, on the taskbar, in web pages, nautilus, etc. However, they seem to come and go, and I can't figure out why. I have disabled shadows (or reduced them to the minimum setting allowed) everywhere I can find a setting, and still the issue persists. I've done quite a bit of searching for a solution, but nothing has consistently worked, and I'm at a loss as to why. I have unchecked 'compositor effects' for Metacity in Configuration Editor, I've zeroed out or reduced as far as allowed all instances of shadow in metacity-theme-1.xml, I've done the same in CompixConfig Settings Manager, all with limited, intermittent success. What else is there, what am I missing?

 My goal is to eliminate ALL shadows, everywhere, all the time. Any help with this would be appreciated. Thanks in advance.

---

### Post by dino99 on 2013-05-17
if you have really purged both unity & compiz, then you should not get that garbage

inside your /home, search about "unity" & "compiz" and erase their subfolders (might be inside some hidden folders: .local/.config/.gnome2/.gconf)

and/or use the System Settings to switch the theme used (adwaita/ambiance/radiance)

---

### Post by antiserious on 2013-05-18
Thanks for the reply. Unity 3D is gone, Compiz is not. Shadows remain, in any theme, even when starting in Low Graphics mode. They're even more prevalent now.
 
It shouldn't be this difficult, and if I can't find a solution I'll have to find another distro. They're too much of a distraction in web pages, nautilus and gedit to be endured.

---

### Post by ibjsb4 on 2013-05-18
You probably seen this.

It does not have any effect if compositing_manager is disabled. 

[ATTACH=CONFIG]242731[/ATTACH]

---

