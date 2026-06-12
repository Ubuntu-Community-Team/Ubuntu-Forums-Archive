---
title: "FreeNX on XGL -&gt; no window decoration on remote desktop"
date: 2006-06-06
forum: Desktop Environments
---

### Post by sander marechal on 2006-06-06
Hello,

I have experienced a weird problem since I upgraded to dapper. I am running Ubuntu dapper with XGL. My parents run Ubuntu breezy, no XGL, just standard desktop. When I connect to my parents computer with FreeNX then two things happen:

1) The window to my parents desktop opens in the next workspace
2) My parents desktop doesn't show any icons or window decorations. Only (themed) buttons with text. There's an empty spot where the icons are supposed to be.

Does anyone have an idea how to solve this? I should add that I replaced my X server with XGL (method B on [https://wiki.ubuntu.com/CompositeManager/Xgl)](https://wiki.ubuntu.com/CompositeManager/Xgl)), I am not running an XGL session on top of the standard X server.

---

### Post by saracen on 2006-08-06
I'm having the same problem.  VNC stopped working after installing XGL so I decided to give FreeNX a shot.  I can now log in with NX but no window decorations or icons show up.  Does anyone know how to solve this?

---

### Post by darrenm on 2006-09-08
Same here. Can anyone suggest a fix? Seems like a protocol compatibility problem between X and XGL

Ta

---

### Post by Crooksey on 2006-09-08
Did you all make XGL the standard Xserver? as opposed to keeping the original xorg aswell?

So do you log into XGL as a session, or have it fron from boot?

If you are starting it from boot and trying to connect to an Xorg box you may have issuses, just log into a session running standard Xorg as the Xserver.

---

### Post by darrenm on 2006-09-08
My setup is: 

Ubuntu Edgy running nxclient 1.5.0-141 as the client with XGL setup as the standard server, xorg not changed. XGL loading from boot.

Ubuntu Dapper running freenx 1.4.0-45-SVN as the server. Tried with XGL and normal X

Tried disabling render in the NX options too, made no difference.

Would you suggest making XGL running as a session then?

---

### Post by sleepkreep on 2006-10-14
This is fixed in the nx 2.1 backend.  Unfortunately there are no ubuntu packages, so you'll have to compile them yourself.

---

