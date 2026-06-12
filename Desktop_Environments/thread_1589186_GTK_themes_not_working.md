---
title: "GTK themes not working"
date: 2010-10-06
forum: Desktop Environments
---

### Post by sundowndk on 2010-10-06
Hi,

I upgraded some packages yesterday on my Ubuntu 10.10, among them was some gnome-settings packages. 

Well, now I got a problem with themes not being applied. Windowborders work fine, but the GTK theme is the default "redmond" style. Icon theme is not applied either. 

Sometimes, maybe every 5th login the theme is applied (Ambiance) and everything works. 

Anyone experienced this problem?

---

### Post by digitography on 2010-10-06
I have a similar problem with 10.04, when I try to change my theme to a clearlooks variant I get "GTK+ theme 'clearlooks' not installed"

yes I know it's no the end of the world, but it is annoying.

---

### Post by wolfe on 2010-10-13
I have the same exact issue as sundowndk

---

### Post by bobowzki on 2010-10-28
I'm having exactly the same problem... Themes are not applied to any windows but the theme selection window.

---

### Post by bobowzki on 2010-10-28
I found a workaround for getting most things right...

Install the package "gtk-theme-switch" and then run it from the terminal

ubuntu$ gtk-theme-switch2

a windows pops up where you can select your favourite gtk theme, and that seems to work for me.

Cheers,
Albin

---

### Post by ShadowMaster22 on 2011-04-26
I had the same problem as sundowndk.  Using Gtk-theme-switch2, i can get the full theme to work about half of the time, as opposed to never.  The downside is that my icon set stays at the default one no matter what.  At first I thought this might have been a problem with gnome-setting-daemon, but I don't think it is anymore.  I didn't have any of these problems before installing my nvidia drivers (and Compiz won't work without the drivers).  I reconfigured /etc/X11/xorg.conf with a fix I found on another forum, but that only worked until I installed some updates.  Hopefully this will be fixed when 11.04 comes out in a couple of days...

---

