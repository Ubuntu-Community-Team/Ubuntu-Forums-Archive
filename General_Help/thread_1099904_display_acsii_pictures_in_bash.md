---
title: "display acsii pictures in bash"
date: 2009-03-18
forum: General Help
---

### Post by mfaust731 on 2009-03-18
hey guys,

I have a ridiculous idea for a old g3 imac that requires me to display images w/o X being loaded, so I need a program that can display jpegs and bmps from a cli - in ascii if at all possible

Anyone know of a good one

---

### Post by geirha on 2009-03-18
There's [aa-project](http://aa-project.sf.net) and [libcaca](http://caca.zoy.org/wiki/libcaca). The latter has color support as well. Try installing [caca-utils](apt:caca-utils) and run ```
cacaview image.jpg
```

---

### Post by mfaust731 on 2009-03-18
got it, however it looks Terrible if im outside of X
after I load X it looks pretty good.

I think I need to enable framebuffer mode, im researching that now

---

### Post by mfaust731 on 2009-03-19
I need some help loading framebuffer, please

---

### Post by KeyserSoze93 on 2009-03-19
Open /boot/grub/menu.lst

Find the lines for your kernel,

Duplicate them.

add the word framebuffer to the title, so you know which one it is.

Add to the end of the kernel line:

```
vga=795
```

Save, and reboot, and select your new option.

---

### Post by Dr Small on 2009-03-19
For your information, here is the framebuffer settings:
```
#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
```

---

