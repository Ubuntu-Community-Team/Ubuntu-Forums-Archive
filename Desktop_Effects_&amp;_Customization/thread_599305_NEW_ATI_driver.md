---
title: "NEW ATI driver"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by hvc123 on 2007-11-01
hey all i have a dell 350 with a ati 9600 installed (AGP)

i have just installed the 8.42.3 drivers and i must say they work pretty good.
until you tell it to use composite and compiz then the graphics get all choppy and the screen flicks like a nutter i cant see any errors anywhere.

this is COMPIZ FUSION WITH AIGLX SUPPORT WITH ATI 8.42.3 drivers.

any help to get smooth compiz effeccts with the new ati drivers NOT using XGL

ta

---

### Post by JBAlaska on 2007-11-01
Have you disabled XGL? 

Also you need to open;
```
gksudo gedit /etc/xdg/compiz/compiz-manager
```

and add "fglrx" to this line, like so;
```
WHITELIST="fglrx"
```


BTW: on my system with a 9600XT I find the new driver to be noticeably slower than XGL was, I'm going to hang tough and hope it gets fixed in 8.43

---

