---
title: "partial picture from screen with Imagemagick in Unity"
date: 2013-12-15
forum: Desktop Environments
---

### Post by jj-retorre on 2013-12-15
Hello,
I cant get a screen shot from my display with the command
```
convert x: show:
```
I got only the part of the display included in the panel or in the dash. The rest of the picture is black.
It works fine with the command
```
convert x:$(xwininfo|grep id:|cut -d "" -f 4) show:
```
when clicking a window, or when I connect to xubuntu.

Should I send a bug report or is it an option to fix  ?

---

