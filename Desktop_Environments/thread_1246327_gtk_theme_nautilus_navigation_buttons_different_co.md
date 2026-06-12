---
title: "gtk theme: nautilus navigation buttons different colors"
date: 2009-08-21
forum: Desktop Environments
---

### Post by k3ttc4r on 2009-08-21
hey guys, looking for your help here ;) 

i'm trying to polish a gtk theme i created a while back. this includes me trying to make the navigation buttons in nautilus a different color from all the other buttons in the theme. i just don't know how to do it, i'm hoping somebody can give me a hint.

attached is a mockup showing what i want to do.

---

### Post by VCoolio on 2009-08-21
Don't know if that's possible: nautilus uses the standard gtk widgets. But according to [this]("http://ubuntuforums.org/showpost.php?p=4513676&postcount=7") you can make a launcher that runs an application (in this case nautilus) with a specific theme like this:

```
sh -c GTK2_RC_FILES=$HOME/.themes/[COLOR="Red"]yourtheme[/COLOR]/gtk-2.0/gtkrc nautilus
```

Just configure your main gtk theme so it fits your wishes for nautilus, save it as another theme and point to that. You can also edit the nautilus launcher in /usr/share/applications if you don't want to create one apart for it.

---

