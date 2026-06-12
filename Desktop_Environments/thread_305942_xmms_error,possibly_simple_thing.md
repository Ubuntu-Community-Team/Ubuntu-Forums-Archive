---
title: "xmms error,possibly simple thing"
date: 2006-11-24
forum: Desktop Environments
---

### Post by muzaki on 2006-11-24
this is my condition: edgy,aiglx,beryl
xmms couldnt be launched,launching it from terminal gets 
Gdk-ERROR **: BadMatch (invalid parameter attributes)
...
...

i did some search and find that this is related to composite being enabled in beryl(XMMS can't go into Double-Size if a composite window manager is active.
)

then i got two ways of solution from other forum:
1. adding alias in .bashrc
      alias xmms='XLIB_SKIP_ARGB_VISUALS=1 xmms' 
from this, i can launch xmms from terminal when using beryl.
But i cant launch it from menu bar, or if other program like streamtuner try to launch it.
2. adding to /etc/profile  this line
        export XLIB_SKIP_ARGB_VISUALS=1
from this, xmms can be launched normally in beryl, but other program will loose its window,

so what i want to try to do is adding something like this in /etc/profile :
if [ "$program" == "xmms" ]; then
    export XLIB_SKIP_ARGB_VISUALS=1
fi


it doesn't work ,hell, i know nothing about programming either, i just want to make this "export XLIB_SKIP_ARGB_VISUALS=1" only executed for xmms, not to all programs.Help me, anyone ](*,)

---

### Post by flugh on 2006-11-24
Write a shellscript with just:
XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/xmms

Save it in ~/bin/xmms

Ensure your $PATH has ~/bin before /usr/bin (look in .bashrc)

Now anything that calls just 'xmms' should call your script and life should be good.

---

### Post by muzaki on 2006-11-24
thanks ,solved :D

---

