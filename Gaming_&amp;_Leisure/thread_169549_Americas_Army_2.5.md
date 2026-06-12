---
title: "Americas Army 2.5"
date: 2006-05-02
forum: Gaming &amp; Leisure
---

### Post by R3linquish3r on 2006-05-02
K so I installed AA after doing a reformat to change around my partitions. When I go to launch it I get this eror which I didn't get last time:

> Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
FGLTexMgr: open of shared memory object failed (Function not implemented)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.

FGLRX is working just fine though...

> spixe@standard-x32:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


Would anyone have any idea what is wrong?

---

### Post by NyTE on 2006-05-02
Americas army is no longer supported for linux dude.

---

### Post by R3linquish3r on 2006-05-03
Yeah I know but 2.5 still plays and there are still servers up/.I found the problem though I didn't have double buffer enabled :P

---

