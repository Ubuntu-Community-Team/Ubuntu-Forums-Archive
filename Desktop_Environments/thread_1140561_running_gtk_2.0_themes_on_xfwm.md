---
title: "running gtk 2.0 themes on xfwm"
date: 2009-04-27
forum: Desktop Environments
---

### Post by atyndall on 2009-04-27
I recently downloaded the Ubuntu Dust theme and extras ([https://wiki.ubuntu.com/Artwork/Incoming/DustTheme)]("https://wiki.ubuntu.com/Artwork/Incoming/DustTheme") to try out on my Xubuntu 9.04 installation.

The problem is that the theme does not apply completely, as the window frames do not change (see Ugly.png and compare to theme photos on wiki page).

I followed the advice I found in another forum, and have the following gtk2-engines packages installed:

[LIST]
[*]gtk2-engines (clearlooks and some)
[*]gtk2-engines-nodoka
[*]gtk2-engines-blueheart
[*]gtk2-engines-murrine
[*]gtk2-engines-xfce
[*]gtk2-engines-ubuntulooks
[*]gtk2-engines-pixbuf
[/LIST]
And this has not helped, the themes are still not applying correctly, even after a restart of Xorg and my computer.

Would anyone be able to provide info on why it is not applying correctly, and how I can rectify this problem?

Much appreciated.

---

### Post by saman on 2009-05-18
As well as a GTK theme, you will also need a theme for xfwm (Xfce Window manager) tp change the window properties.

---

### Post by mcduck on 2009-05-18
> **atyndall said:**
> I recently downloaded the Ubuntu Dust theme and extras ([https://wiki.ubuntu.com/Artwork/Incoming/DustTheme)]("https://wiki.ubuntu.com/Artwork/Incoming/DustTheme") to try out on my Xubuntu 9.04 installation.

The problem is that the theme does not apply completely, as the window frames do not change (see Ugly.png and compare to theme photos on wiki page).

I followed the advice I found in another forum, and have the following gtk2-engines packages installed:

[LIST]
[*]gtk2-engines (clearlooks and some)
[*]gtk2-engines-nodoka
[*]gtk2-engines-blueheart
[*]gtk2-engines-murrine
[*]gtk2-engines-xfce
[*]gtk2-engines-ubuntulooks
[*]gtk2-engines-pixbuf
[/LIST]
And this has not helped, the themes are still not applying correctly, even after a restart of Xorg and my computer.

Would anyone be able to provide info on why it is not applying correctly, and how I can rectify this problem?

Much appreciated.
GTK doesn't have anything to do with window borders. Not even in Gnome. So your GTK theme is definitely not going to affect your window borders with any other DE/window manager either.

To change window borders you need to use themes for your window manager.

---

