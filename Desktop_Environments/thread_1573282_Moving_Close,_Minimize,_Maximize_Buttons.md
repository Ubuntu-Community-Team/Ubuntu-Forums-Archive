---
title: "Moving Close, Minimize, Maximize Buttons"
date: 2010-09-12
forum: Desktop Environments
---

### Post by bryanfblareunion on 2010-09-12
I have ubuntu 10.04 and installed a theme that I really love. However, this theme puts the buttons in the top-right corner of the window (close, minimize, maximize) is there any way to move them back to the left?

---

### Post by dv3500ea on 2010-09-12
Press Alt-F2.
Enter ```
gconf-editor
```.
Edit /apps/metacity/general/button_layout to 'close,minimize,maximize:'.

or
Run:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout 'close,minimize,maximize:'
```

---

### Post by wiz2010 on 2010-09-13
Yes as [dv3500ea]("http://ubuntuforums.org/member.php?u=906606") said it can be changed in gconf-editor
but it will reset if you change the theme.

[http://deb-info.blogspot.com/2010/08/window-title-bar-back-to-right-in.html](http://deb-info.blogspot.com/2010/08/window-title-bar-back-to-right-in.html)

wiz2010

---

