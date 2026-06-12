---
title: "Emerald does not work"
date: 2007-04-23
forum: Desktop Environments
---

### Post by MF Ryan on 2007-04-23
i just replaced my IBM P200 moniter with a SCEPTRE X20. beryl works just fine, but the Window Decorator does not work. it loads windows without the bars at the top. my new resolution is 1680x1050. 

does anyone know how to get the Window Decorator to Work

---

### Post by Gillingham on 2007-04-24
I'm in a similar position as are quite a few people.  It looks like quite a few steps that are missing we probably need a troubleshooting thread somewhere as the answers are out there.

Check the [Desktop effects and customization]("http://ubuntuforums.org/forumdisplay.php?f=223") forum for the various threads.

I'm currently at work but when I get home I'll try a couple of things:

1) emerald --replace

and

2) append the following to your /etc/X11/xorg.conf in the “Device” section:
```


Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
```

I hope one of these works for us :)

---

### Post by Gillingham on 2007-04-24
Ok doing emerald --replace and changing the rendering path (under advanced Beryl options) to copy (from automatic) seems to have worked.

---

### Post by shrinux on 2007-12-29
[SIZE="3"]Hi Freedom Desktop Users :)

I just found the title reflects exactly my situation, therefore, I preferred to post my problem here !!!


        [SIZE="2"]  [COLOR="Green"]_Laptop:_
          Fujetsu Siemens > Amilo Pro > V2000

          _Graphics Card:_
          Intel Graphics Card

          _OS Tree:_
          Unix > Linux > Debian > Ubuntu > Xubuntu 7.10 > Xfce 4.4.2[/COLOR][/SIZE]


Problem:

I installed Compiz Fusion with Emerald as illustrated in deferent forums, but when I replace Compiz, the decorative windows vanish !!!
I try then to replace Emerald using the terminal but it gives me an error:
[COLOR="Red"](emerald:5880) : Wnck-WARNING ** : Property _NET_WM_NAME contained invalid UTF-8[/COLOR]


Thanks
Sharif
[/SIZE]

---

### Post by Gillingham on 2007-12-29
I'm not sure about this problem - one thing to check is that I notice you are using 7.10 the Gusty Gibbon - my problems were with 7.04 the Feisty Fawn.  You may wish to check that the guides you are following are for the right version.  Unfortunately I'm using Gnome rather than XFCE so can't point you in the right direction

Good luck and I hope some more helpful person will be along shortly.

---

