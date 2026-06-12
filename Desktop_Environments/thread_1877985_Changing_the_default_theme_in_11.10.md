---
title: "Changing the default theme in 11.10"
date: 2011-11-09
forum: Desktop Environments
---

### Post by UsmanKhan on 2011-11-09
Hello every one.
I want to change the default 11.10 unity Ambiance theme to another but there is no option except the 4 preinstalled themes (ambiance,radiance,high contrast,highcontrastinverse).

How could i download new themes in unity and is it possible in the this version??

NOTE
(I like unity and don't want to change to genome)

---

### Post by mcduck on 2011-11-09
Install the [apt:gnome-tweak-tool]("apt:gnome-tweak-tool"), and get some GTK3 themes from gnome-look.org. Preferably ones that also include a GTK2 theme so even the old applications not yet updated to use GTK3 will get correct theme. Extract the theme into ~/.themes (for GTK and Metacity themes) or ~/.icons (for icon themes) and enable it with gnome-tweak-tool.

Gnome-tweak-tool will appear as "Advanced Settings" in the Dash, and allows you to adjust some of the settings not available by default in Gnome 3, like selecting GTK, icon and window border themes separately, configuring your fonts etc.

---

### Post by UsmanKhan on 2011-11-09
> **mcduck said:**
> Install the [apt:gnome-tweak-tool](apt:gnome-tweak-tool), and get some GTK3 themes from gnome-look.org. Preferably ones that also include a GTK2 theme so even the old applications not yet updated to use GTK3 will get correct theme. Extract the theme into ~/.themes (for GTK and Metacity themes) or ~/.icons (for icon themes) and enable it with gnome-tweak-tool.

Gnome-tweak-tool will appear as "Advanced Settings" in the Dash, and allows you to adjust some of the settings not available by default in Gnome 3, like selecting GTK, icon and window border themes separately, configuring your fonts etc.

Thanks for the reply bro.
but i m type of newbie so can u elaborate how i can but them into themes folder because the one i found in usr/share/themes gives permision denied.?

---

### Post by mcduck on 2011-11-09
> **UsmanKhan said:**
> Thanks for the reply bro.
but i m type of newbie so can u elaborate how i can but them into themes folder because the one i found in usr/share/themes gives permision denied.?

Both ~/.themes and ~/.icons are inside your home directory (the "~" tells that) and hidden directories (as the name starts with a "."). So just go to your home and press Ctrl-H to show hidden files.

What comes to the permission problem with system directories, you should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by UsmanKhan on 2011-11-09
Thanks a lot 
It worked :P

---

