---
title: "xmodmap periodic resets"
date: 2011-07-31
forum: Desktop Environments
---

### Post by suy on 2011-07-31
I'm running Xubuntu 11.04 and i'm using a KeyOvation mac compatible Gold Touch keyboard. Because the weird ordering of Ctrl, option, and the apple key, I wanted to remap the keys to my liking using xmodmap. Here's the settings file i'm using. 

```

remove mod4 = Super_L
remove mod4 = Super_R
remove control = Control_L
remove control = Control_R
remove mod1 = Alt_L
remove mod1 = Alt_R
keysym Control_L = Super_L
keysym Control_R = Super_R
keysym Super_L = Alt_L
keysym Super_R = Alt_R
keysym Alt_L = Control_L
keysym Alt_R = Control_R
add control = Control_L
add control = Control_R
add mod4 = Super_L
add mod4 = Super_R
add mod1 = Alt_L
add mod1 = Alt_R

```

It works great when I call xmodmap on it. However, after a few minutes, the settings will no longer work and revert to the default settings and I have to call xmodmap again to get it to work. What could be the causes for this?

I've tried looking around a bit for this problem with little success. [[COLOR="Red"]One guy[/COLOR]]("http://ubuntuforums.org/showthread.php?t=286934") claimed that he got around this by removing scim and I prefer not to do that. 

Thanks in advance

---

