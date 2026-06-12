---
title: "[LXDE] Composite key doesn't work when I use two keyboard layouts"
date: 2013-10-06
forum: Desktop Environments
---

### Post by igurev on 2013-10-06
Hello,

I am trying LXDE on Ubuntu 12.04 and I really like it. There is just one annoying thing that I would like to get rid of.

Since I need to use two different keyboard layouts - Italian and Norwegian - I have added the "Keyboard layout switch" applet on the panel and then, via terminal, I have set the two keyboard layouts in this way:

```
gksu leafpad /etc/xdg/lxsession/LXDE/autostart
```

and then I added this line:

```
@setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll it,no
```


Everything seemed to work properly, but then I discovered that when I am using the Italian keyboard layout, the "Alt Gr" button doesn't work anymore as a composite key. Since I am using "Alt Gr" pretty often, I would like to find a way to fix this problem.


I am using also "gnome-session-fallback" and "E17", but I am having this problem just on LXDE.

---

