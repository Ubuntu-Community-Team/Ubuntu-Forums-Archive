---
title: "GTK theme not changeable in Oneiric"
date: 2011-10-30
forum: Desktop Environments
---

### Post by rosslaird on 2011-10-30
When I use the ubuntu tweak tool to (try to) change the GTK theme on one of my systems (not both; this works on the other system), or when I use gtk-chtheme to try to accomplish the same thing, the window elements change but the window titlebar and icons do not. I can select and change the theme, and some elements will change (scroll bars, window colors, etc.), but the titlebars and buttons always remain stuck in the Ambiance theme.

As I mentioned, one of my systems does not have this problem. On that system, the theme switch works on the buttons as well. Both are running Oneiric -- however, one was a clean install (the one that's working) and one was an upgrade from Natty.

I have searched the forums (and the web) but cannot find this problem noted anywhere.

---

### Post by vasa1 on 2011-10-30
> **rosslaird said:**
> ...
I have searched the forums (and the web) but cannot find this problem noted anywhere.

Did you come across this:
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html) ?

---

### Post by mcduck on 2011-10-30
The thing here is that window title bars and icons are not part of the GTK theme, so it's just normal that changing your GTK theme doesn't affect those. ;)

(It's also possible to save a complete theme, which defines at least GTK, Metacity and icon themes, and also possibly both mouse cursor theme and wallpaper image. These complete themes are usually cause for the confusion about a certain theme not changing everything. It's rather rare to find a downloadable complete theme, so you usually just get one of the theme components instead)

Window borders are controlled by Metacity theme (by default) and icons are defined by icon theme.

Also pay attention to GTK themes you use, GTK2 themes will of course not work for GTK3 applications and GTK3 themes have no effect on GTK2 applications. So you should try to sue themes that include both GTK2 and GTK3 support.

Edit: gtk-chtheme only works for GTK2, not for GTK3. And if you use Gnome Shell you need to log out and back again after changing your window border theme.

---

### Post by rosslaird on 2011-10-30
Thanks for the tips. I always find the crossover between GTK (with its variants), compiz, and Metacity to be very confusing.

I discovered the source of the problem using gconf-editor. The theme is listed in two places:

Apps --> Metacity --> General

and

Desktop --> Gnome --> Interface

On my system, the first setting said "Adwaita" and the second setting said "Radiance." I changed the second one to Adwaita, rebooted (logging off/on would probably have done it too, I assume), and now Adwaita shows up in the buttons.

Thanks again for the help.

---

