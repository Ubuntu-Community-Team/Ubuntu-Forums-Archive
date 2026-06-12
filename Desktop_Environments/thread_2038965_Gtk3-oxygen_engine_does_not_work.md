---
title: "Gtk3-oxygen engine does not work"
date: 2012-08-07
forum: Desktop Environments
---

### Post by vip562 on 2012-08-07
I installed the kde-plasma-desktop package on ubuntu 12.04. After I installed the DE I seem to have theme issues with Firefox, Thunderbird, Chrome, etc. I then installed the gtk3 oxygen engine and still there was no fix to the theme. Gtk2 apps seem to work fine in kde (like nautilus). Is there a reason why the Gtk3 oxygen engine does not work?

---

### Post by Jakin on 2012-08-07
Have you made a folder in .config (hidden folder in home directory)?


place a folder inside ".config" name it gtk-3.0 -

then place a empty text file inside "gtk-3.0" name it settings.ini

paste 

 [Settings]
gtk-theme-name = oxygen-gtk

and save in "settings.ini" then reboot and it should now be themed, this works for me anyway.

---

### Post by vip562 on 2012-08-07
Unfortunately, that did not work for me.

---

