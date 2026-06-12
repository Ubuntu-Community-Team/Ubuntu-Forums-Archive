---
title: "Wine Problems"
date: 2006-09-21
forum: Gaming &amp; Leisure
---

### Post by Ferrat on 2006-09-21
Well I'll explain this in order so you know exactlly what I've done =)

Began with a clean and uptodate (2006-09-20) installation of Ubuntu, fixed my videodrivers to ATi and compiled a new kernel for 3Dacc, works like a charm.

Followed this guide 
[http://ubuntuforums.org/showthread.php?t=243336](http://ubuntuforums.org/showthread.php?t=243336)

To install Wine to get my WoW to work 

Running in OpenGL gave this problem ($ wine WoW.exe -opengl) 
```

This application has encountered a critical error:
ERROR #132 (0x85100084) Fatal Exception
Program: C:\Program Files\World of Warcraft\WoW.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:00000000
The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".
```

So I tried running in Direct3D 
Worked, some small issues tho, like freezing 0,5seconds when targeting and some buildings hade graficissues with the 3D models but other than that no real biggies, FPS 40 and so on. 

But in a attempt to fix the OpenGL problem to remove the freezing and maybe help the graficissues I followed this guide adressing just those issues 

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

How ever when checking before compiling I got this Warning. 

```

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

```

and I get this error with both D3D and OpenGL now  

```

err:module:import_dll Library OPENGL32.dll (which is needed by L"Z:\\home\\iceblock\\Desktop\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\iceblock\\Desktop\\World of Warcraft\\WoW.exe" failed, status c0000135

``` 

Well the guide adresses this as a common problem 

> 
Problem #1 - opengl32 not found when running wow.exe

You installed the patch,compiled and installed wine & wow then when you try to run wow you get the
following error message which may also mention glu32 as well as opengl32 not being found:

[email]guest@linux:~/.wine[/email]/drive_c/Program Files/World of Warcraft> wine wow.exe

err:module:import_dll Library OPENGL32.dll (which is needed by L"C:Program Files/World of
Warcraft/wow.exe") not found err:module:LdrInitializeThunk Main exe initialization for L"C:/Program
Files/World of Warcraft/wow.exe" failed, status c0000135

Solution : check that /usr/local/lib/wine/opengl32.dll.so has ownership of root:root and permissions
-rwxr-xr-x, if it does not then you may have not been super user when you ran the "make install" command.
become superuser and repeat the make install command as shown in the howto. Do not just change the
ownership/permissions of opengl32.dll.so as probably all the other files are wrong too, so do a make install.


Now I've tried this and I've been doing "make install" with sudo but to no help, I think the problem lies in compiling Wine with no D3D or OpenGl but not sure how to fix that and why the guide get the same error as me. 


Any help would be great =)

---

### Post by Ferrat on 2006-09-21
Update:

Found the problem, I was missing some libs ect for building *doh* recompiling now, update if it works or not coming =)

EDIT: 
Worked like a charm =) Wow Running now just a few bugs with both d3d and OpenGL so not really ready to switch from Windows but soon =)

---

