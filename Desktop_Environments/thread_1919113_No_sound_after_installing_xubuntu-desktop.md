---
title: "No sound after installing xubuntu-desktop"
date: 2012-02-02
forum: Desktop Environments
---

### Post by Lars Noodén on 2012-02-02
I've installed xubuntu-desktop on top of a basic Lubuntu install.  The sound was working before, but now has ceased to play.  What do I change to get the sound playing again in Xubuntu?  

Switching between LXDE and XFCE makes no difference.

---

### Post by Lars Noodén on 2012-02-03
I couldn't find any setting to change that made a difference.  A clumsy workaround was to wipe the system and then add only XFCE4 to Lubuntu, not xubuntu-desktop.

---

### Post by GraeW on 2012-02-03
I actually noticed some differences between the xubuntu-desktop meta package, and the xfce4 meta, when I was toying around with installs. I actually ran into an issue with the xubuntu version which made me lose all window decorations - I had no titlebars or other options on opened programs. When I wiped and reinstalled (for other reasons than this issue) I instead went with the xfce4 package and have not had a problem since (going on a month since the rebuild).
 
the only thing I can think of is something is flagged differently as a dependency for the sound, and isn't set up properly or conflicts with something else installed with the default ubuntu/gnome/unity combination. 
 
Although some may say don't delete and reinstall, I find when all else fails and you know you won't really lose personal information, go for the full removal and start over.

---

