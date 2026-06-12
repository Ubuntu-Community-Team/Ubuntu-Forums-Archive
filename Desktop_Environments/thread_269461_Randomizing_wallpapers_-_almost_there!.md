---
title: "Randomizing wallpapers - almost there!"
date: 2006-10-01
forum: Desktop Environments
---

### Post by liquilife on 2006-10-01
I am running the Gnome desktop and I am trying to set up a script that will change my desktop wallpaper every 5 minutes. I found this little script posted in the howto several months ago. It is technically working but it's not doing quite what I want. I have several wallpapers configured in Gnome to appropriately stretch, zoom, center or tile for each wallpaper and for some I have some gradient backgrounds set to match the colors of that particular wallpaper. The script below doesn't automate that. Anyone have any clues how this could be done to randomize the wallpaper and honor the gnome wallpaper settings for each one it displays? Thanks!
```
#!/bin/bash

while [ 1 == 1 ]
do
ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g' | grep $HOME` )
RANGE=${#ALIST[@]}
let "number = $RANDOM % $RANGE"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}
sleep 300
done
```

---

### Post by lagagnon on 2006-10-02
> **liquilife said:**
> I am running the Gnome desktop and I am trying to set up a script that will change my desktop wallpaper every 5 minutes.
How annoying!
> 
Anyone have any clues how this could be done to randomize the wallpaper and honor the gnome wallpaper settings for each one it displays?


I doubt very much that is possible as your script would have to somehow detect the settings and graphic type.

---

