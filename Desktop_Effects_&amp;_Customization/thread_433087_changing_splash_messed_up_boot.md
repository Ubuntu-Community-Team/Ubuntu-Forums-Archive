---
title: "changing splash messed up boot?"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by yourearthlymaster on 2007-05-04
I followed a guide to change the splash screen, and now my comp won't boot up right.  
the commands typed were:  ```
gconf-editor /apps/gnome-session/options
```
then I changed the default location to /home/name/.gnome2/splash.png

now i can only boot in recovery mode.  Anyone know how I can fix this?
 
NEVER MIND:  i got it
use ```
gconftool-2 --type string --set /apps/gnome-session/options/splash_image "insert path"
```

---

