---
title: "gamma correction fglrx"
date: 2006-03-06
forum: Desktop Environments
---

### Post by yyagol on 2006-03-06
Hi
i have an ATI 9200 se . 
for long time i have neglect the problem.
everytime i install the fglrx the gamma go creasy, and it is too bright.
and the desktop is blure ( exept for the mouse pointer )
i try to fix that in many ways but its impossible to fix it.
i try to add gamma correction to the xorg.conf,
i try to xgamma -gamma.
nothing helps
c :
```
$ fglrxinfoRe: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1050 (X4.3.0-8.22.5)
$ grep gamma /var/log/Xorg.0.log
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)

```
My xorg.conf says nothing about gamma correction !!!!!
how can it be fix ?
i know the gamma correction is "on" by default
but cant be shut down !?:confused:

---

