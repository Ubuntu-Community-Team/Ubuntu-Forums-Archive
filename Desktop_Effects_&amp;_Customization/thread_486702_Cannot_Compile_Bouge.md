---
title: "Cannot Compile Bouge"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by Razer on 2007-06-28
My effects after installing compiz fusion were a little slow so I tried the instructions in the Compiz fusion sticky but when I try to compile bouge it does not work. It only gives me this

```
razer@razer-ubuntu:~$ cd /home/razer/Desktop/bouge
razer@razer-ubuntu:~/Desktop/bouge$ make; make install
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.lo/bin/sh: libtool: not found
make: *** [build/libbouge.lo] Error 127
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.lo/bin/sh: libtool: not found
make: *** [build/libbouge.lo] Error 127
razer@razer-ubuntu:~/Desktop/bouge$ 
razer@razer-ubuntu:~/Desktop/bouge$ 



```

---

### Post by Razer on 2007-06-28
I also have the 3 files that I needed before I started to compile. I have libxslt1.1 libxslt1-dev compiz-dev.

---

### Post by jbizzler on 2007-09-05
Sorry to dig this up, but I must say, same here:

```
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.lobouge.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
bouge.c:93: error: expected specifier-qualifier-list before 'PaintWindowProc'
bouge.c:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitiate'
bouge.c:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveTerminate'
bouge.c:264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveGetYConstrainRegion'
bouge.c: In function 'moveHandleMotionEvent':
bouge.c:357: error: dereferencing pointer to incomplete type
bouge.c:357: error: dereferencing pointer to incomplete type
bouge.c:359: error: 'MoveScreen' has no member named 'grabIndex'
bouge.c:364: error: dereferencing pointer to incomplete type
bouge.c:366: error: 'MoveDisplay' has no member named 'w'
bouge.c:368: error: 'MoveDisplay' has no member named 'x'
bouge.c:368: error: 'lastPointerX' undeclared (first use in this function)
bouge.c:368: error: (Each undeclared identifier is reported only once
bouge.c:368: error: for each function it appears in.)
bouge.c:369: error: 'MoveDisplay' has no member named 'y'
bouge.c:369: error: 'lastPointerY' undeclared (first use in this function)
bouge.c:371: error: dereferencing pointer to incomplete type
bouge.c:371: error: 'CompWindowTypeFullscreenMask' undeclared (first use in this function)
bouge.c:377: error: 'XRectangle' undeclared (first use in this function)
bouge.c:377: error: expected ';' before 'workArea'
bouge.c:380: error: 'MoveDisplay' has no member named 'x'
bouge.c:381: error: 'MoveDisplay' has no member named 'y'
bouge.c:383: warning: implicit declaration of function 'getWorkareaForOutput'
bouge.c:384: warning: implicit declaration of function 'outputDeviceForWindow'
bouge.c:385: error: 'workArea' undeclared (first use in this function)
bouge.c:387: error: 'MoveDisplay' has no member named 'opt'
bouge.c:389: error: 'MoveDisplay' has no member named 'region'
bouge.c:390: error: 'MoveDisplay' has no member named 'region'
bouge.c:390: warning: implicit declaration of function 'moveGetYConstrainRegion'
bouge.c:395: error: 'MoveDisplay' has no member named 'region'
bouge.c:400: error: dereferencing pointer to incomplete type
bouge.c:400: error: dereferencing pointer to incomplete type
bouge.c:401: error: dereferencing pointer to incomplete type
bouge.c:401: error: dereferencing pointer to incomplete type
bouge.c:402: error: dereferencing pointer to incomplete type
bouge.c:402: error: dereferencing pointer to incomplete type
bouge.c:402: error: dereferencing pointer to incomplete type
bouge.c:403: error: dereferencing pointer to incomplete type
bouge.c:403: error: dereferencing pointer to incomplete type
bouge.c:405: warning: implicit declaration of function 'XRectInRegion'
bouge.c:405: error: 'MoveDisplay' has no member named 'region'
bouge.c:408: error: 'MoveDisplay' has no member named 'status'
bouge.c:408: error: 'RectangleIn' undeclared (first use in this function)
bouge.c:414: error: 'MoveDisplay' has no member named 'region'
bouge.c:421: error: dereferencing pointer to incomplete type
bouge.c:421: error: dereferencing pointer to incomplete type
bouge.c:426: error: 'MoveDisplay' has no member named 'region'
bouge.c:433: error: dereferencing pointer to incomplete type
bouge.c:433: error: dereferencing pointer to incomplete type
bouge.c:438: error: 'MoveDisplay' has no member named 'status'
bouge.c:443: error: 'MoveDisplay' has no member named 'opt'
bouge.c:445: error: dereferencing pointer to incomplete type
bouge.c:445: error: 'CompWindowStateMaximizedVertMask' undeclared (first use in this function)
bouge.c:447: error: 'MoveScreen' has no member named 'snapOffY'
bouge.c:449: error: dereferencing pointer to incomplete type
bouge.c:451: error: dereferencing pointer to incomplete type
bouge.c:451: error: 'CWX' undeclared (first use in this function)
bouge.c:451: error: 'CWY' undeclared (first use in this function)
bouge.c:453: error: dereferencing pointer to incomplete type
bouge.c:453: error: 'CWWidth' undeclared (first use in this function)
bouge.c:454: error: dereferencing pointer to incomplete type
bouge.c:456: error: dereferencing pointer to incomplete type
bouge.c:457: error: dereferencing pointer to incomplete type
bouge.c:457: error: dereferencing pointer to incomplete type
bouge.c:459: error: 'MoveDisplay' has no member named 'x'
bouge.c:459: error: 'MoveDisplay' has no member named 'y'
bouge.c:461: warning: implicit declaration of function 'maximizeWindow'
bouge.c:463: error: 'MoveScreen' has no member named 'snapOffY'
bouge.c:463: error: 'MoveScreen' has no member named 'snapBackY'
bouge.c:468: error: 'MoveScreen' has no member named 'origState'
bouge.c:470: error: 'MoveScreen' has no member named 'snapBackY'
bouge.c:472: warning: implicit declaration of function 'otherScreenGrabExist'
bouge.c:479: warning: implicit declaration of function 'syncWindowPosition'
bouge.c:481: error: 'MoveScreen' has no member named 'origState'
bouge.c:483: error: dereferencing pointer to incomplete type
bouge.c:484: error: dereferencing pointer to incomplete type
bouge.c:486: warning: implicit declaration of function 'warpPointer'
bouge.c:486: error: 'pointerY' undeclared (first use in this function)
bouge.c:494: error: dereferencing pointer to incomplete type
bouge.c:496: error: dereferencing pointer to incomplete type
bouge.c:498: error: dereferencing pointer to incomplete type
bouge.c:498: error: dereferencing pointer to incomplete type
bouge.c:499: error: dereferencing pointer to incomplete type
bouge.c:501: error: dereferencing pointer to incomplete type
bouge.c:502: error: dereferencing pointer to incomplete type
bouge.c:503: error: dereferencing pointer to incomplete type
bouge.c:504: error: dereferencing pointer to incomplete type
bouge.c:507: error: dereferencing pointer to incomplete type
bouge.c:507: error: 'CompWindowStateMaximizedHorzMask' undeclared (first use in this function)
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:512: error: dereferencing pointer to incomplete type
bouge.c:512: error: dereferencing pointer to incomplete type
bouge.c:512: error: dereferencing pointer to incomplete type
bouge.c:515: error: dereferencing pointer to incomplete type
bouge.c:517: error: dereferencing pointer to incomplete type
bouge.c:517: error: dereferencing pointer to incomplete type
bouge.c:518: error: dereferencing pointer to incomplete type
bouge.c:520: error: dereferencing pointer to incomplete type
bouge.c:521: error: dereferencing pointer to incomplete type
bouge.c:522: error: dereferencing pointer to incomplete type
bouge.c:523: error: dereferencing pointer to incomplete type
bouge.c:527: warning: implicit declaration of function 'moveWindow'
bouge.c:527: error: 'MoveDisplay' has no member named 'w'
bouge.c:527: error: 'TRUE' undeclared (first use in this function)
bouge.c:527: error: 'FALSE' undeclared (first use in this function)
bouge.c:529: error: 'MoveDisplay' has no member named 'x'
bouge.c:530: error: 'MoveDisplay' has no member named 'y'
bouge.c: At top level:
bouge.c:536: error: expected declaration specifiers or '...' before 'XEvent'
bouge.c: In function 'moveHandleEvent':
bouge.c:540: error: dereferencing pointer to incomplete type
bouge.c:542: error: 'event' undeclared (first use in this function)
bouge.c:543: error: 'ButtonPress' undeclared (first use in this function)
bouge.c:544: warning: implicit declaration of function 'findScreenAtDisplay'
bouge.c:544: warning: assignment makes pointer from integer without a cast
bouge.c:547: error: dereferencing pointer to incomplete type
bouge.c:547: error: dereferencing pointer to incomplete type
bouge.c:549: error: 'MoveScreen' has no member named 'grabIndex'
bouge.c:551: warning: implicit declaration of function 'moveTerminate'
bouge.c:552: error: 'MoveDisplay' has no member named 'opt'
bouge.c:557: error: 'KeyPress' undeclared (first use in this function)
bouge.c:558: error: 'KeyRelease' undeclared (first use in this function)
bouge.c:559: warning: assignment makes pointer from integer without a cast
bouge.c:562: error: dereferencing pointer to incomplete type
bouge.c:562: error: dereferencing pointer to incomplete type
bouge.c:564: error: 'MoveScreen' has no member named 'grabIndex'
bouge.c:570: error: 'MoveDisplay' has no member named 'key'
bouge.c:572: warning: implicit declaration of function 'XWarpPointer'
bouge.c:572: error: dereferencing pointer to incomplete type
bouge.c:572: error: 'None' undeclared (first use in this function)
bouge.c:581: error: 'MotionNotify' undeclared (first use in this function)
bouge.c:582: warning: assignment makes pointer from integer without a cast
bouge.c:584: error: 'pointerX' undeclared (first use in this function)
bouge.c:584: error: 'pointerY' undeclared (first use in this function)
bouge.c:586: error: 'EnterNotify' undeclared (first use in this function)
bouge.c:587: error: 'LeaveNotify' undeclared (first use in this function)
bouge.c:588: warning: assignment makes pointer from integer without a cast
bouge.c:592: error: 'ClientMessage' undeclared (first use in this function)
bouge.c:593: error: dereferencing pointer to incomplete type
bouge.c:597: error: 'WmMoveResizeMove' undeclared (first use in this function)
bouge.c:598: error: 'WmMoveResizeMoveKeyboard' undeclared (first use in this function)
bouge.c:600: warning: implicit declaration of function 'findWindowAtDisplay'
bouge.c:600: warning: assignment makes pointer from integer without a cast
bouge.c:603: error: array type has incomplete element type
bouge.c:605: error: 'CompAction' undeclared (first use in this function)
bouge.c:605: error: 'action' undeclared (first use in this function)
bouge.c:606: error: 'MoveDisplay' has no member named 'opt'
bouge.c:614: warning: implicit declaration of function 'moveInitiate'
bouge.c:615: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:621: error: 'Window' undeclared (first use in this function)
bouge.c:621: error: expected ';' before 'root'
bouge.c:624: warning: implicit declaration of function 'XQueryPointer'
bouge.c:624: error: dereferencing pointer to incomplete type
bouge.c:624: error: dereferencing pointer to incomplete type
bouge.c:625: error: 'root' undeclared (first use in this function)
bouge.c:625: error: 'child' undeclared (first use in this function)
bouge.c:629: error: 'Button1Mask' undeclared (first use in this function)
bouge.c:645: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:648: error: dereferencing pointer to incomplete type
bouge.c:603: warning: unused variable 'o'
bouge.c:655: error: 'DestroyNotify' undeclared (first use in this function)
bouge.c:656: error: 'MoveDisplay' has no member named 'w'
bouge.c:656: error: 'MoveDisplay' has no member named 'w'
bouge.c:658: error: 'MoveDisplay' has no member named 'opt'
bouge.c:661: error: 'UnmapNotify' undeclared (first use in this function)
bouge.c:662: error: 'MoveDisplay' has no member named 'w'
bouge.c:662: error: 'MoveDisplay' has no member named 'w'
bouge.c:664: error: 'MoveDisplay' has no member named 'opt'
bouge.c:670: warning: implicit declaration of function 'UNWRAP'
bouge.c:670: error: 'handleEvent' undeclared (first use in this function)
bouge.c:671: error: dereferencing pointer to incomplete type
bouge.c:672: warning: implicit declaration of function 'WRAP'
bouge.c: At top level:
bouge.c:676: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'movePaintWindow'
bouge.c:711: error: expected declaration specifiers or '...' before 'Display'
bouge.c: In function 'moveDisplayInitOptions':
bouge.c:715: error: 'MoveDisplay' has no member named 'opt'
bouge.c:716: error: dereferencing pointer to incomplete type
bouge.c:717: error: dereferencing pointer to incomplete type
bouge.c:718: error: dereferencing pointer to incomplete type
bouge.c:718: error: 'moveInitiate' undeclared (first use in this function)
bouge.c:719: error: dereferencing pointer to incomplete type
bouge.c:719: error: 'moveTerminate' undeclared (first use in this function)
bouge.c:720: error: dereferencing pointer to incomplete type
bouge.c:720: error: 'FALSE' undeclared (first use in this function)
bouge.c:721: error: dereferencing pointer to incomplete type
bouge.c:722: error: dereferencing pointer to incomplete type
bouge.c:722: error: 'CompBindingTypeButton' undeclared (first use in this function)
bouge.c:723: error: dereferencing pointer to incomplete type
bouge.c:723: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:724: error: dereferencing pointer to incomplete type
bouge.c:724: error: 'CompAltMask' undeclared (first use in this function)
bouge.c:725: error: dereferencing pointer to incomplete type
bouge.c:725: error: 'Button1' undeclared (first use in this function)
bouge.c:726: error: dereferencing pointer to incomplete type
bouge.c:726: error: 'CompBindingTypeKey' undeclared (first use in this function)
bouge.c:727: error: dereferencing pointer to incomplete type
bouge.c:727: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:728: error: dereferencing pointer to incomplete type
bouge.c:729: error: dereferencing pointer to incomplete type
bouge.c:730: warning: implicit declaration of function 'XKeysymToKeycode'
bouge.c:730: error: 'display' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XStringToKeysym'
bouge.c:732: error: 'MoveDisplay' has no member named 'opt'
bouge.c:733: error: dereferencing pointer to incomplete type
bouge.c:734: error: dereferencing pointer to incomplete type
bouge.c:735: error: dereferencing pointer to incomplete type
bouge.c:736: error: dereferencing pointer to incomplete type
bouge.c:737: error: dereferencing pointer to incomplete type
bouge.c:739: error: 'MoveDisplay' has no member named 'opt'
bouge.c:740: error: dereferencing pointer to incomplete type
bouge.c:741: error: dereferencing pointer to incomplete type
bouge.c:742: error: dereferencing pointer to incomplete type
bouge.c:744: error: 'MoveDisplay' has no member named 'opt'
bouge.c:745: error: dereferencing pointer to incomplete type
bouge.c:746: error: dereferencing pointer to incomplete type
bouge.c:747: error: dereferencing pointer to incomplete type
bouge.c: In function 'moveGetDisplayOptions':
bouge.c:755: error: dereferencing pointer to incomplete type
bouge.c:757: error: 'MoveDisplay' has no member named 'opt'
bouge.c:757: error: invalid application of 'sizeof' to incomplete type 'CompOption' 
bouge.c:758: error: 'MoveDisplay' has no member named 'opt'
bouge.c:759: warning: control reaches end of non-void function
bouge.c: At top level:
bouge.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveSetDisplayOption'
bouge.c:798: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitDisplay'
bouge.c: In function 'moveFiniDisplay':
bouge.c:838: error: dereferencing pointer to incomplete type
bouge.c:840: warning: implicit declaration of function 'freeScreenPrivateIndex'
bouge.c:842: error: 'handleEvent' undeclared (first use in this function)
bouge.c: At top level:
bouge.c:848: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitScreen'
bouge.c: In function 'moveFiniScreen':
bouge.c:876: error: dereferencing pointer to incomplete type
bouge.c:876: error: dereferencing pointer to incomplete type
bouge.c:877: error: dereferencing pointer to incomplete type
bouge.c:879: warning: implicit declaration of function 'removeScreenAction'
bouge.c:880: error: 'MoveDisplay' has no member named 'opt'
bouge.c:882: error: 'paintWindow' undeclared (first use in this function)
bouge.c:884: error: 'MoveScreen' has no member named 'moveCursor'
bouge.c:885: warning: implicit declaration of function 'XFreeCursor'
bouge.c:885: error: dereferencing pointer to incomplete type
bouge.c:885: error: 'MoveScreen' has no member named 'moveCursor'
bouge.c: At top level:
bouge.c:891: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInit'
bouge.c: In function 'moveFini':
bouge.c:904: warning: implicit declaration of function 'freeDisplayPrivateIndex'
bouge.c: In function 'moveGetVersion':
bouge.c:911: error: 'ABIVERSION' undeclared (first use in this function)
bouge.c:912: warning: control reaches end of non-void function
bouge.c: At top level:
bouge.c:919: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveVTable'
bouge.c:941: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libbouge.lo] Error 1
```

---

