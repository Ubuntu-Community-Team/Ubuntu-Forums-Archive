---
title: "qstick install (problem) for Quake 3 gamepad"
date: 2005-10-24
forum: Gaming &amp; Leisure
---

### Post by speckone on 2005-10-24
In an attempt to get gamepad functionality in Quake 3 Arena, I've been trying to install [qstick]("http://www.ditch.org/kbstick/"). I get the following message when I do a make:

```
speckone@ubuntulaptop:~/kbstick-0.80$ make
cc -I/usr/X11R6/include  -L/usr/X11R6/lib -lX11 -lXtst -o kbstick kbstick.c
kbstick.c: In function ‘help’:
kbstick.c:96: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c: In function ‘cmdLine’:
kbstick.c:107: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:115: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:117: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c: In function ‘initJoystick’:
kbstick.c:136: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:140: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c: In function ‘getXDisplay’:
kbstick.c:152: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:155: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:158: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:161: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:163: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c: In function ‘assignCodes’:
kbstick.c:180: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:213: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:221: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:231: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:238: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c: In function ‘readLoop’:
kbstick.c:269: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:273: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c: In function ‘cleanup’:
kbstick.c:352: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:353: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c: In function ‘main’:
kbstick.c:365: warning: incompatible implicit declaration of built-in function ‘printf’
kbstick.c:375: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:377: warning: incompatible implicit declaration of built-in function ‘strcpy’
kbstick.c:378: warning: incompatible implicit declaration of built-in function ‘strcat’
kbstick.c:384: warning: incompatible implicit declaration of built-in function ‘exit’
kbstick.c:405: warning: incompatible implicit declaration of built-in function ‘exit’
speckone@ubuntulaptop:~/kbstick-0.80$ ./qstick
./qstick: line 112: kbstick: command not found

```

Any ideas or alternative meathods to gamepad functionality?
Thanks

---

