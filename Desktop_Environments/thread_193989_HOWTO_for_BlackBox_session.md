---
title: "HOWTO for BlackBox session?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Isoss on 2006-06-10
Hey

I love this blackbox. although it's too simple, but it's so usefull to me when I need to focus on doing one thing like developing a website. but I am having some issues with it, like I can't type in arabic or get to any of the system adminstration applications. I'd like to know how to start any of the system adminstration or preferences, I know by typing the application name like totem or firefox I can get it to fire up! So I need a you to learn how to manage everything using terminal so I won't need to return to the normal desktop!

Thanks in advance guys. I hope that you'd also recommend some HOWTO for BlackBox, that'll be easier for me so I can take it as a manual.

---

### Post by TOPPEL on 2006-06-10
i dont know anything about blackbox ?  do you like or have tried fluxbox and do you know if that would be better for you ?  or how about XFCE ?  to be honest i dont know how you got blackbox working in the first place unless you launch by XDM.

---

### Post by Isoss on 2006-06-11
I found the solution.
I simply edited /etc/X11/xorg.conf and at the keboard section I replaced         ```
Option      "XkbLayout" "us"
``` with  ```
Option      "XkbLayout" "us,ar"
```
And then added the following:
```

        Option      "XkbOptions" "grp:ctrl_shift_toggle"
        Option      "XkbOptions" "grp:shift_toggle,grp_led:scroll"

```
And that's it!
Thanks and I hope this will help others who had the same problem with the layout.
[quote="TOPPEL"]
i dont know anything about blackbox ? do you like or have tried fluxbox and do you know if that would be better for you ? or how about XFCE ? to be honest i dont know how you got blackbox working in the first place unless you launch by XDM.[/quote]
I tried XFCE and FluxBox and I like them. But blackbox is much simple. Anyway I don't know what is XDM, I just installed it with synaptic and it worked.

---

### Post by matata on 2006-06-12
[QUOTE=Isoss]
I tried XFCE and FluxBox and I like them. But blackbox is much simple. Anyway I don't know what is XDM, I just installed it with synaptic and it worked.[/QUOTE]

try iceWM it have alot of options and menus than Blackbox and it's simple.

XDM= X Display Manager , it's like KDM or GDM.

---

