---
title: "Stable VNC / Remote Desktop server for Xubuntu?"
date: 2009-12-10
forum: Desktop Environments
---

### Post by mac666 on 2009-12-10
Hey
I have Xubuntu karmic and i installed x11vnc to have as remote desktop (the xubuntu machine is a server without screen, but needs to have desktop environment)
 
but x11vnc crashes / shutsdown after a while(i dont know exactly how long but its less then 24 hours run time)
 
I have no idea why it dies, but i would like to have a more Ubuntu kind of way remote desktop environment; Stable and integreted in the environment.
 
Any ideas?
The runetime needs to be unlimited, since i only will reboot every 2 months...
 
EDIT: Or a Script that runs x11vnc everytime to proccess dies :)

---

### Post by mac666 on 2009-12-11
Anyone must know?

---

### Post by krunge on 2009-12-12
Could you supply the full x11vnc output including when it terminates?

Please attach it to the post as a file instead of pasting it all in.

---

### Post by mac666 on 2009-12-12
Where would this log be?

I havent activated any sort of log...

---

### Post by krunge on 2009-12-12
> Where would this log be?

I havent activated any sort of log...
The easiest way is to add something like "-o /tmp/x11vnc.log" to the x11vnc command line.  Then induce the problem you have described.  Then upload that x11vnc.log file to this thread.

---

