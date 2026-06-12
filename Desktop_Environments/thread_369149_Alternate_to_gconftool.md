---
title: "Alternate to gconftool?"
date: 2007-02-24
forum: Desktop Environments
---

### Post by hansoffate on 2007-02-24
I am supposed to do this for a howto:
sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button2/' /etc/X11/xkb/symbols/pc
gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/enable true
gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/mousekeys_enable true

and alot of the rest of the tutorial has gconftool.  What can i use in kde? The tutorial is here:  [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Thanks for the help,
Hans

---

### Post by louis_nichols on 2007-02-24
gconf(tool) is specific to Gnome. In theory, if you have a KDE only system, you can not and need not use gconf and anything related to it. If your desktop is hybrid KDE and Gnome, then just (install and) use gconftool.

---

### Post by hansoffate on 2007-02-24
The tutorial requires me to use gconftool in order to fully setup my macbook.  How do i install regular ubuntu?  Maybe i should just downgrade to edgy.  Is there an easy way to make my system to 6.10 kubuntu and ubuntu from 7.04 kubuntu?

Thanks,
-hans

---

