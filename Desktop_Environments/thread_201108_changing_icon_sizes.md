---
title: "changing icon sizes ?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by colinw on 2006-06-21
Is there a way to globally change the icon sizes so that any window you go into is affected ?

I know you can zoom in and zoom out in a window, but that only affects that window.

I just find the icons too big really for most most themes, so i want to set them to small.

Thanks....

---

### Post by colinw on 2006-06-21
ok sorry to bother you, i find out where to change it now.

Thanks... :)

---

### Post by jamesford on 2006-06-21
make a new file in your homedir called .gtkrc-2.0
paste:
-----------
gtk-icon-sizes = 
"panel-menu=22,22:
panel=22,22:
gtk-menu=16,16:
gtk-large-toolbar=22,22:
gtk-button=16,16"
---------
change the sizes until you find something that suits you.

ps only works on newly opened apps, you may have to restart gnome to see changes made to the panel menu etc

once you have found sizes that suits you you can do:
sudo cp ~/.gtkrc-2.0 /root
to make root apps also use the icon sizes you have chosen

keep in mind that icons can look blurry if you choose sizes not supported by your icon theme, most themes support 16, 22 and 24, some also 20 and 18 iirc

---

