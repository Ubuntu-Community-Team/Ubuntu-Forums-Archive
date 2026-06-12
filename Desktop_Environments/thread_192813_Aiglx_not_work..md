---
title: "Aiglx not work."
date: 2006-06-09
forum: Desktop Environments
---

### Post by killbill on 2006-06-09
Hi,  anybody know how to solve these problem?
I used to have aiglx+compiz work well following this tutorial.
[http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)  
(intel 845G, direct rendering enabled.)

1 .  I deleted " /etc/xdg/autostart/compiz..", and now when I do as the tutorial, there's no such file in my folder. 


2. why it's  compiz.. , but not compiz-aiglx as the tutorial mentioned? Does it work? Before I delete compiz in /etc/xdg/autostart,  all the titles of my windows were gone, and just like metacity without title bar.

My current status: 
```

glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x31
direct rendering: Yes

```
```

tobey@ubuntu:~$ compiz start
tobey@ubuntu:~$ compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

```
```

tobey@ubuntu:~$ compiz start --replace
tobey@ubuntu:~$ libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x31
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```
no title bar for windows, and no panels.

---

### Post by leohart on 2006-06-09
No title bar is actually normal. I followed that thread and my title (gnome-window-decorator) is gone. You need to hold Alt and click to move your window.

You can turn decorator on in compiz and title will be back. Regarding the other porblem, I don't know.

---

