---
title: "Lots of compiz processes/instances"
date: 2007-11-27
forum: Desktop Environments
---

### Post by devzero on 2007-11-27
Hi,

I have on another place Ubuntu 7.10 32 bit installed (upgraded from 7.04)

and realised if I do a ps aux |grep compiz -> compiz.txt vim tells me, that I have

15178 lines of: 
martin   20861  0.0  0.0   1756   524 ?        S    11:44   0:00 /bin/sh /usr/bin/compiz

pstree shows:

&#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;compiz&#9472;&#9472;&#9472;+


The Graphic Card is a GMA 965 (82Q963/Q965 Integrated Graphics Controller)

CPU is a Core2Duo 6600/ 2,4GHZ

The many processes are here just compiz started.

There a more of identically pcs upgrade from 7.04 zu 7.10, but there isn that
problem.

How can I diagnose what causes that process flood?

If you need some more details I will post it asap.

Thanks for your help.

---

### Post by zanzer7 on 2007-11-27
what output do you get from compiz? You can try running it in a terminal:

```
$ compiz

and

$ compiz.real --replace
```

I really don't know a lot about this, but I figured I might as well try to help

---

### Post by devzero on 2007-11-27
i tried to run "compiz" and i got:

```


/home/martin/.config/compiz/compiz-manager: 1: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Checking for Xgl: /usr/bin/compiz: 352: Cannot fork
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Checking for Xgl: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reachedXlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Maximum number of clients reachedxvinfo:  Unable to open display :0.0

xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Maximum number of clients reachedMaximum number of clients reached

xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0

xvinfo:  Unable to open display :0.0
xvinfo:  Unable to open display :0.0
Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
xvinfo:  Unable to open display :0.0
not present. 
Blacklisted PCIID '8086:2992' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Fenstermanager-Warnung: Thema »ClearlooksAlternative« konnte nicht geladen werden: Es konnte keine gültige Datei für das Thema »ClearlooksAlternative« gefunden werden

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2992' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Fenstermanager-Warnung: Thema »ClearlooksAlternative« konnte nicht geladen werden: Es konnte keine gültige Datei für das Thema »ClearlooksAlternative« gefunden werden

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

the screen begins to flicker, the windows apprears and disapears all time.

i could kill that with control c and i went back to normal.

---

### Post by zanzer7 on 2007-11-28
> **devzero said:**
> i tried to run "compiz" and i got:

```

...

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
**Checking for Xgl: not present.**
Blacklisted PCIID '8086:2992' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
**Checking for Xgl: not present.**
Starting gtk-window-decorator
Fenstermanager-Warnung: Thema »ClearlooksAlternative« konnte nicht geladen werden: 
```


Not having xgl installed might be (read: is) a problem.

Try running```
apt-get install xserver-xgl
```and restart your session.

If that doesn't fix the problem, please paste /etc/X11/xorg.conf here.

---

### Post by devzero on 2007-11-29
Hmm the weird thing is, compiz works, but it has that many processes....


My xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82Q963/Q965 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "AccelMethod"           "XAA"
        Option          "RenderAccel"           "true"
        Option          "XAANoOffscreenPixmaps" "true"
        Option          "AllowGLXWithcomposite" "true"
        Option          "TripleBuffer"          "true"
        Option          "DRI"                   "true"
        Option          "DDC"                   "true"
        Option          "XVideo"                "true"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       33-81
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82Q963/Q965 Integrated Graphics Controller"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by devzero on 2007-12-13
/bump

---

### Post by KernelPanic14 on 2008-04-16
> **devzero said:**
> Hi,

I have on another place Ubuntu 7.10 32 bit installed (upgraded from 7.04)

and realised if I do a ps aux |grep compiz -> compiz.txt vim tells me, that I have

15178 lines of: 
martin   20861  0.0  0.0   1756   524 ?        S    11:44   0:00 /bin/sh /usr/bin/compiz
...

Edit /usr/bin/compiz as root

```
sudo nano /usr/bin/compiz
```Look for COMPIZ_NAME and replace "compiz" with "compiz.real". Using "compiz" the script /usr/bin/compiz is just relaunching itself.

It will not fix the 352.

Enjoy ;)

---

