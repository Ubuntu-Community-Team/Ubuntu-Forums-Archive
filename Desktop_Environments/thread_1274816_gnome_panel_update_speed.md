---
title: "gnome panel update speed"
date: 2009-09-25
forum: Desktop Environments
---

### Post by to3000 on 2009-09-25
hello,
i have a script that changes my wallpaper every 2 seconds.
```

#!/bin/bash

while [ 1 ]

do

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/tom/walpapers/red.jpg
sleep 2

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/tom/walpapers/yellow.jpg
sleep 2

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/tom/walpapers/purple.jpg
sleep 2

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/tom/walpapers/blue.jpg
sleep 2

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/tom/walpapers/green.jpg
sleep 2

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/tom/walpapers/orange.jpg
sleep 2

done


```
when my wallpaper changes my transparent panels delay the change (see attached)

i have also tried compiz but that makes the icons transparent and i don't want that

is there any way is could fix this so that they change at the same time.
thanx

ps i know "walpapers" is wrong

---

### Post by Giblet5 on 2009-09-25
You could try forcing a refresh via: ```
xrefresh
``` but that'll make the whole screen flicker.

You could turn off the transparency and use a panel background image to achieve a pleasing and consistent visual effect.

You could edit all the images to place a margin at the top/bottom with an ideal gradient.

You could set up compiz correctly and run a transparent screensaver or movie against a gradient background using xwinwrap (makes icons "transparent" - actually, they're partially obscured)

The list of possibilities approaches the infinite.

---

