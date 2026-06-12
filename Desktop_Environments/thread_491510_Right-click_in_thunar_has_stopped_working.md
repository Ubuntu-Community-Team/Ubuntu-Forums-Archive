---
title: "Right-click in thunar has stopped working"
date: 2007-07-03
forum: Desktop Environments
---

### Post by kjur on 2007-07-03
Hi All,

In my Xubuntu right-click in a main panel of Thunar has stopped working. I mean as long as right button is pressed I can see the menu, but it disappears when right button is released. It works as normal in a side pane and in all the system. Just doesn't want to work in thunar.

Any ideas how to fix it?

I have deleted Thunar settings from ~/.config/Thunar , but it's still the same

My system is Xubuntu 7.04 with all available updates (no updates recently, when it's stopped working)

Much appreciated for any help,

Thanks,
Greg

---

### Post by The Recorder on 2007-08-25
This is Theme related.  It happens to me when I use Aurora themes.  Haven't found a solution other than changing themes.

---

### Post by grumpybuffalo on 2008-05-27
I also came across this problem, and I have come up with a quick fix. I modified the theme so that it doesn't apply to list widgets, and list widgets use the xfce-dawn theme instead - I kinda like that one. It isn't a perfect solution, but it is better than using a different theme.

I've attached the gtkrc file; unpack the attachment, go to the folder where the Aurora theme is (/usr/share/themes/Aurora maybe), go into the gtk-2.0 folder, and replace the gtkrc file with the one inside the archive I attached.

EDIT: not sure why it was working earlier, but this didn't even fix the problem... arg...

---

