---
title: "Beryl stopped working Please help"
date: 2007-03-15
forum: Desktop Effects &amp; Customization
---

### Post by AnthonyJK@gmail.com on 2007-03-15
Hello I've been running beryl all day and now it suddenly stopped working and now when i type beryl manager in terminal i get this

anthonyjk@AnthonyJK:~$ beryl-manager
anthonyjk@AnthonyJK:~$ libGL warning: 3D driver claims to not support visual 0x5b


I dont know if this has to do with it but it happend immediately after I tried to enable right click with this code

sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button2/' /etc/X11/xkb/symbols/pc
gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/enable true
gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/mousekeys_enable true

from this post

[http://ubuntuforums.org/showthread.php?t=359655&highlight=two+finger+click](http://ubuntuforums.org/showthread.php?t=359655&highlight=two+finger+click)

is there a way i can undo whatever i did or any solution at all?

Im so frustrated I've reinstalled Ubuntu 4  times in the past 2 days :confused: 

any help would be greatly appreciated

---

