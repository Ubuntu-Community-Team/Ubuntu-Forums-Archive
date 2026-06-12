---
title: "i3 WM intel driver issues"
date: 2023-12-16
forum: Desktop Environments
---

### Post by bakarba on 2023-12-16
Hello! I've been having trouble with i3 and my intel drivers. When I first installed i3 there would sometimes be a garbled mess for a few seconds when I switched work-spaces before it went to normal. I tried modifying my 20-intel.conf file but now some apps like discord and Alacritty have weird see-through bars in them. I would include a picture but whenever I try it tells me that I have an unverified token. I would really appreciate some help (I am using picom as a compositor).

My 20-intel.conf:
```

Section "Device"
     Identifier "Intel Graphics" 
     Driver "intel" 
    Option "TearFree" "true" 
EndSection

```

---

### Post by bakarba on 2023-12-17
I have now installed kde and the same thing is happening in there, so Im gonna delete the .conf file

---

