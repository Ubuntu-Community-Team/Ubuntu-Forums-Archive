---
title: "aterm: can't load &quot;Black&quot;, colorID = 0, (29)"
date: 2006-04-27
forum: Desktop Environments
---

### Post by psycho78 on 2006-04-27
hi everybody... , 

i don't know what I did that this happened.. but when i try to start several programs, i get strange messages about color...e.g. aterm says:

aterm: can't load "Black", colorID = 0, (29),

xterm says:
Warning: Color name "black" is not defined
Warning: Color name "gray60" is not defined
Warning: Cannot convert arguments to displayList function "foreground"
Warning: Cannot convert string "foreground      gray90;lines           1,-1,-1,-1,-1,1;foreground      gray60;lines           -1,0,0,0,0,-1" to type XawDisplayList

and does not show any white color .... 

does anyone know how I can solve this? I already downloaded a "new" rgb.txt and added the path to xorg.conf, but that did not help... :(

---

### Post by elizabeth on 2006-08-19
I just had this problem, the following solved my problem:

```
sudo apt-get install xrgb
```

---

