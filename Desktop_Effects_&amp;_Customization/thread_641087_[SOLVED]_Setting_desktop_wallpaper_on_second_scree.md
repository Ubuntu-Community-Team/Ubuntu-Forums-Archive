---
title: "[SOLVED] Setting desktop wallpaper on second screen"
date: 2007-12-15
forum: Desktop Effects &amp; Customization
---

### Post by navaburo on 2007-12-15
EDIT: SOLUTION:

```

DISPLAY=:0.0 fbsetbg -f ~/img/gits.png 
DISPLAY=:0.1 fbsetbg -f ~/img/virus.jpg

```


orig post follows:

I have two X screens,:0.0 and :0.1. 

When I do:
 ```
feh --bg-center
```
the bg changes on the 0 screen, but not on the 1 screen.

But, when i use firefox to set the bg, it sets on both screens.

How can I independantly control the bg on each screen from the command line?

(i tried DISPLAY=:0.1 feh --bg-center, but it seems to ignore the DISPLAY variable)

---

