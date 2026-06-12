---
title: "Tom Clancy's Rainbow Six: Rogue Spear"
date: 2006-12-25
forum: Gaming &amp; Leisure
---

### Post by xenoalien on 2006-12-25
How would I install a game called Tom Clancy's Rainbow Six: Rogue Spear?

---

### Post by pay on 2006-12-25
You would need to use either wine or cedega (you could try cvs for free). Unfortuantley it was voted to not work on the wine app database, however those version used are rather old, you might have more luck. [http://appdb.winehq.org/appview.php?iVersionId=2821](http://appdb.winehq.org/appview.php?iVersionId=2821)

---

### Post by xenoalien on 2006-12-25
I have Wine Windows Emulator installed. That website:   [http://appdb.winehq.org/appview.php?iVersionId=2821](http://appdb.winehq.org/appview.php?iVersionId=2821)
Says that wine is able to emulate it. How would I browse to the files in the cd because when I try and open it, it displays a playlist as if it is a music CD. It does have Music (cda files) But it also contains data files that I would like to get to. Is there anyway to browse the CD?

---

### Post by pay on 2006-12-25
You should be able to install it with ```
wine /media/cdrom0/Setup.exe
```

---

### Post by xenoalien on 2006-12-25
I get some errors though:

xenoalien@xeno:~$ wine /media/cdrom0/Setup.exe
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e9e0000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000f, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e9ed000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
wine: Critical section 7e9ed000 wait failed at address 0x7efaddf0 (thread 000c), starting debugger...
wine: Critical section 7e9e0000 wait failed at address 0x7efaddf0 (thread 000f), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
00000012 
        00000013    0
0000000d (D) (null)
        0000000f    0
        0000000e    0
0000000a 
        0000000c    0
        0000000b    0
wine client error:e: write: Bad file descriptor
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) (null)
        0000000c    0
        0000000b    0
wine client error:b: write: Bad file descriptor
xenoalien@xeno:~$ 

 
Any ideas? :-k

---

### Post by xenoalien on 2006-12-25
Something about OpenGL? Can this be fixed? :-k ](*,) :-k ](*,) :-k

---

### Post by pay on 2006-12-25
Yes. Make sure that you have your drivers setup correctly and that you have direct rendering```
glxinfo | grep direct rendering
```

---

### Post by xenoalien on 2006-12-25
I just reinstalled Ubuntu and I have not installed any drivers....

this is what I get when I enter the command:

xenoalien@xeno:~$ glxinfo | grep direct rendering
grep: rendering: No such file or directory
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
xenoalien@xeno:~$ 

I have NvidiaGLX installed but how do I install direct rendering?

---

### Post by xenoalien on 2006-12-25
Could my xorg.conf file be configured wrong?

---

### Post by xenoalien on 2006-12-25
I attached my xorg.conf file. See if there are any problems with it. Thanks

---

### Post by xenoalien on 2006-12-25
Alright, I fixed the opengl problem. I then mounted the game with Cedega and wined the setup.exe from the cdrom0 directory. And I installed it (full) and it asked me to install directx I clicked no and finish. Then I did wine autorun.exe and  clicked play, now it says:

xenoalien@xeno:/media/cdrom0$ wine autorun.exe
xenoalien@xeno:/media/cdrom0$ ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Any Ideas?

---

### Post by haxer on 2006-12-25
Thats the problem with linux at all direct x games almost everyone you may forget sorry dude i noticed the same thing on lots of direct x games try something else "opengl" games is tha **** for linux works fine :)

---

### Post by maruchan on 2006-12-25
Try out the newest (today's) WINE build, it fixes a directx problem.

---

### Post by stevejesus on 2007-11-09
Wine Is Not an Emulator.

Just thought I should share.

---

