---
title: "Gnome Themes Problem After update"
date: 2008-05-14
forum: Desktop Environments
---

### Post by Trystam on 2008-05-14
After having upgraded Gutsy to Hardy, the weirdest thing has started to happend.
Every time i reboot the theme is reset to the default, but going into appearnce the darklooks appears as selected, the only way to get the theme again is to customize, change and reapply .

Anyone having this problem aswell ?

Rgds

FC

---

### Post by n_ops on 2008-07-29
> **Trystam said:**
> 
Every time i reboot the theme is reset to the default, but going into appearnce the darklooks appears as selected, the only way to get the theme again is to customize, change and reapply.
FC

I had the same problem with Darklooks when I installed Hardy.

The following fixed the problem for me:

```
cd /usr/share/themes/Darklooks/gtk-2.0/
```

and then:

```
gedit gtkrc
```

In the theme file that opens change lines 181 and 182 from

bg[NORMAL] = @tooltip_bg_color
fg[NORMAL] = @tooltip_fg_color

to:

bg[NORMAL] = @tooltips_bg_color
fg[NORMAL] = @tooltips_fg_color

(i.e. add an 's' after tooltip in the second half)
That edit fixed the issue for me.

You can also find this fix, and a number of other fixes for dark themes in general at:
[http://opencomputing.blogspot.com/2008/05/using-dark-theme-in-ubuntu.html](http://opencomputing.blogspot.com/2008/05/using-dark-theme-in-ubuntu.html)

---

