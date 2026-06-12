---
title: "Switch between gnome themes?"
date: 2011-03-13
forum: Desktop Environments
---

### Post by Biddlesby on 2011-03-13
Hello all, as I do a bit of programming now and then, I have been experimenting with dark contrast colour schemes for all of my text editors and so on. But I have been finding that the "Darklooks" gnome theme is not so great when surfing the web, if webmasters have been a little lazy with their CSS.

So I am looking for a terminal command or shortcut of some fashion that I can use to switch between a dark and light gnome theme.

Any help much appreciated,

Harry

---

### Post by Frogs Hair on 2011-03-13
This may be of interest ```
sudo apt-get-install gtk-theme-switch
```
to use from the terminal use the command ```
gtk-theme-switch2
```

---

### Post by mcduck on 2011-03-14
Another option is to use gconftool-2 to change the gconf key that sets the theme. Gconftool-2 should be installed by default.

---

