---
title: "Wolfenstein &quot;Sys_Error: Couldn't load default.cfg&quot;"
date: 2008-05-25
forum: Gaming &amp; Leisure
---

### Post by cokehabit on 2008-05-25
Trying to run Wolfenstein I get ```
george@michelle-desktop:~$ wolfsp 
Wolf 1.41 linux-i386 Dec  4 2002
----- FS_Startup -----
Current search path:
/home/george/.wolf/main
/usr/local/games/wolfenstein/main/sp_pak3.pk3 (14 files)
/usr/local/games/wolfenstein/main/sp_pak2.pk3 (232 files)
/usr/local/games/wolfenstein/main

----------------------
246 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg

```

I've had a look and I can't see what's wrong...

---

### Post by cokehabit on 2008-05-28
surely this must have come up before?

---

### Post by Ziggy Stardust on 2008-05-28
According to [http://zerowing.idsoftware.com](http://zerowing.idsoftware.com) this error is due to missing .pk3 files. I've had some of these errors in both quake3 and RTCW. Are you sure you copied all the .pk3s to the right location?

It does indeed look suspicious that the engine is only able to locate sp_pak3.pk3 and sp_pak2.pk3.

I'm in Windows at the moment, trying to install kde 4.1 beta, but I can have a look at it later tonight or tomorrow if you're sure that you've copied all the .pk3s from the cd to the right location.

---

### Post by jw5801 on 2009-01-25
If you're still having this issue (or if anyone else finds it), check the permissions on the .pk3 files. I'm not sure about Ubuntu, but in Gentoo they should be owned by the root user and the games group.```
chown -R root:games /opt/rtcw/main
chmod -R g+r /opt/rtcw/main
```Is what I had to do to fix it. But they're in a different place in Ubuntu, and they may need to be owned by a different group.

---

