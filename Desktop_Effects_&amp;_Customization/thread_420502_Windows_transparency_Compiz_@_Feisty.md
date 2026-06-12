---
title: "Windows transparency: Compiz @ Feisty"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by wampirek on 2007-04-23
Hello, 

One simple question: how to make inactive windows to be half transparent? I mean not only title bars, but whole windows. 
I know that using mouse wheel while holding ALT-key works, but I'd like inactive windows to become half-transparent immediately when they become inactive (some other window goes at the top). 

I don't want to install and configure Beryl, I'd like to use Compiz, as it is installed together with Feisty. I've installed compiz-manager, but cannot find this option there... 

Hope anyone knows the answer :)

---

### Post by wampirek on 2007-04-25
Noone knows the answer? I don't believe ;)

---

### Post by amgeex on 2007-04-28
You need something called trans-inactive. You have to download and compile it yourself, but its very easy. Check [http://www.compiz.org](http://www.compiz.org), click on the Documentation tab at the top, and search for the "Tips, Tricks & HowTo's" category, the "Smooth window transitions" tutorial should be there.

---

### Post by wampirek on 2007-05-13
Thanx! It works great :) 
Unfortunatelly when I have (for example) MPlayer in a window (not fullscreen) and some other window becomes active, I can't see the movie any more - it becomes black. When MPLayer becomes active - the movie can be seen again. 
Is there any way to make some windows not become transparent?

---

### Post by rohan! on 2007-05-27
i've tried to use the tip, but get this output:

```
rohan@$ wget http://www.anykeysoftware.co.uk/compiz/trans-inactive/trans-inactive.c && gcc -o trans-inactive trans-inactive.c -L/usr/X11R6/lib -lX11 && sudo cp trans-inactive /usr/bin/ && rm trans-inactive trans-inactive.c

--13:48:37--  http://www.anykeysoftware.co.uk/compiz/trans-inactive/trans-inactive.c
           => `trans-inactive.c.2'
Resolving www.anykeysoftware.co.uk... 212.227.64.112
Connecting to www.anykeysoftware.co.uk|212.227.64.112|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,107 (11K) [text/plain]

100%[==============================================================================================================================>] 11,107        55.23K/s             

13:48:37 (55.05 KB/s) - `trans-inactive.c.2' saved [11107/11107]

trans-inactive.c:25:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from trans-inactive.c:26:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
trans-inactive.c:28:20: error: getopt.h: No such file or directory
trans-inactive.c:30:19: error: X11/X.h: No such file or directory
trans-inactive.c:31:22: error: X11/Xlib.h: No such file or directory
trans-inactive.c:32:23: error: X11/Xatom.h: No such file or directory
trans-inactive.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_window_type’
trans-inactive.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_active_win’
trans-inactive.c:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
trans-inactive.c:116: error: expected ‘)’ before ‘*’ token
trans-inactive.c:126: error: expected ‘)’ before ‘*’ token
trans-inactive.c: In function ‘usage’:
trans-inactive.c:135: warning: incompatible implicit declaration of built-in function ‘printf’
trans-inactive.c: In function ‘main’:
trans-inactive.c:147: error: ‘Display’ undeclared (first use in this function)
trans-inactive.c:147: error: (Each undeclared identifier is reported only once
trans-inactive.c:147: error: for each function it appears in.)
trans-inactive.c:147: error: ‘dpy’ undeclared (first use in this function)
trans-inactive.c:148: error: ‘Window’ undeclared (first use in this function)
trans-inactive.c:148: error: expected ‘;’ before ‘root’
trans-inactive.c:149: error: ‘XWindowAttributes’ undeclared (first use in this function)
trans-inactive.c:149: error: expected ‘;’ before ‘attr’
trans-inactive.c:151: error: ‘Atom’ undeclared (first use in this function)
trans-inactive.c:151: error: expected ‘;’ before ‘_NET_ACTIVE_WINDOW’
trans-inactive.c:153: error: ‘XEvent’ undeclared (first use in this function)
trans-inactive.c:153: error: expected ‘;’ before ‘xev’
trans-inactive.c:160: error: array type has incomplete element type
trans-inactive.c:161: error: ‘NULL’ undeclared (first use in this function)
trans-inactive.c:178: error: ‘optarg’ undeclared (first use in this function)
trans-inactive.c:179: warning: incompatible implicit declaration of built-in function ‘sscanf’
trans-inactive.c:179: error: ‘EOF’ undeclared (first use in this function)
trans-inactive.c:180: warning: incompatible implicit declaration of built-in function ‘fprintf’
trans-inactive.c:180: error: ‘stderr’ undeclared (first use in this function)
trans-inactive.c:189: warning: incompatible implicit declaration of built-in function ‘sscanf’
trans-inactive.c:190: warning: incompatible implicit declaration of built-in function ‘fprintf’
trans-inactive.c:203: warning: incompatible implicit declaration of built-in function ‘printf’
trans-inactive.c:210: warning: incompatible implicit declaration of built-in function ‘fprintf’
trans-inactive.c:214: error: ‘err_noop’ undeclared (first use in this function)
trans-inactive.c:216: error: ‘root’ undeclared (first use in this function)
trans-inactive.c:217: error: ‘attr’ undeclared (first use in this function)
trans-inactive.c:219: error: ‘PropertyChangeMask’ undeclared (first use in this function)
trans-inactive.c:219: error: ‘StructureNotifyMask’ undeclared (first use in this function)
trans-inactive.c:220: error: ‘SubstructureNotifyMask’ undeclared (first use in this function)
trans-inactive.c:222: error: ‘_NET_WM_WINDOW_OPACITY’ undeclared (first use in this function)
trans-inactive.c:222: error: ‘False’ undeclared (first use in this function)
trans-inactive.c:223: error: ‘_NET_ACTIVE_WINDOW’ undeclared (first use in this function)
trans-inactive.c:224: error: ‘_NET_WM_WINDOW_TYPE’ undeclared (first use in this function)
trans-inactive.c:225: error: ‘_NET_WM_WINDOW_TYPE_DESKTOP’ undeclared (first use in this function)
trans-inactive.c:228: error: ‘_NET_WM_WINDOW_TYPE_UTILITY’ undeclared (first use in this function)
trans-inactive.c:231: error: ‘_NET_WM_WINDOW_TYPE_DOCK’ undeclared (first use in this function)
trans-inactive.c:234: error: ‘old_active_window’ undeclared (first use in this function)
trans-inactive.c:236: error: ‘toplevels’ undeclared (first use in this function)
trans-inactive.c:247: error: ‘window_type’ undeclared (first use in this function)
trans-inactive.c:258: error: ‘True’ undeclared (first use in this function)
trans-inactive.c:269: error: ‘xev’ undeclared (first use in this function)
trans-inactive.c:271: error: ‘PropertyNotify’ undeclared (first use in this function)
trans-inactive.c:278: error: ‘active_window’ undeclared (first use in this function)
trans-inactive.c:281: error: ‘None’ undeclared (first use in this function)
trans-inactive.c:306: error: ‘MapNotify’ undeclared (first use in this function)
trans-inactive.c:325: error: ‘UnmapNotify’ undeclared (first use in this function)

```

:(

---

### Post by rohan! on 2007-05-27
ok, fixed. installed xorg-dev. :) it does look pretty good!

---

