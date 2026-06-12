---
title: "Cannot install DCOM98 using Winetool!!!"
date: 2006-09-24
forum: Desktop Environments
---

### Post by coolradar on 2006-09-24
I installed the newest Ubuntu several days ago. Everything work very well excpt wine. I cannot install DCOM98 by using Winetool. The installation always died and a pop-up window said:  

The wine debugger was startet. If you installation does not continue for a while you should switch to the console where you stated winetools from to debug or let me kill it to continue here. Sometimes you don't have to do anything to continue.

The problem is I always get this error. The debug information is like below. Hope someone can help me sort it out

Thanks!


detecting Wine version... done.
Drive C: is /home/ruida/.wine/drive_c
Wine 0.9.21
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.21".
Calls to wine are executed as  "wine".
Config is /home/ruida/.wine/winetools.log.
Choice is Base setup
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/ruida/.wine/winetools.log
1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
waiting for wineservers to exit...
err:ntdll:RtlpWaitForCriticalSection section 0x7e933fc0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000e, blocked by 000b, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x16ab0c "?" wait timed out in thread 000b, blocked by 000e, retrying (60 sec)

wine: Critical section 7e933fc0 wait failed at address 0x7efb0030 (thread 000e), starting debugger...
WineDbg starting on pid 0xa
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for winex11<elf>
Unhandled exception: wait failed on critical section 0x7e933fc0 X11DRV_CritSection
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7efb0030
wine client error:b: write: Bad file descriptor
Process of pid=0x0000000a has terminated

---

