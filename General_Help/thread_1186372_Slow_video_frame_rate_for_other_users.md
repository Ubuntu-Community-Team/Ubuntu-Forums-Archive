---
title: "Slow video frame rate for other users"
date: 2009-06-13
forum: General Help
---

### Post by GrootBrak on 2009-06-13
I have always seem to get this problem. The main user have a fully funtional desktop when playing games. But always when the other non sudo users log in, even straight from boot, they can't play any games because the frame rate is too slow. I have the same problem with my Acer netbook. Only the user that is set up with boot seems to have a decent video frame rate. My 6.04 Ubuntu I got to work, but had to do a lot of adding lines and stuff, but I cannot recall how to do it. I think in any case this is a bug with Ubuntu. All users should have the same video setting, right?

---

### Post by 3rdalbum on 2009-06-13
System > Administration > Users And Groups

Click "Unlock" and put in your password. Click on one of the affected users, and click Properties. Under the "User Privileges" tab, make sure "Capture video from TV or Webcams, and use 3D acceleration" is ticked. I suspect it's not ticked for your other users, and this is causing low performance.

Your Acer netbook will not have decent frame rates anyway if you're running Ubuntu 9.04. It has one of Intel's slowest GPUs, underclocked to save battery life. And Ubuntu 9.04's Intel driver currently has low performance - they are in the process of re-writing the driver to deal with the new infrastructure in X. Once the re-writing is done, the driver will have better performance than it has before; but this work might not be pushed to 9.04 users.

---

### Post by GrootBrak on 2009-06-17
I actually checked the settings for other users first. It made no difference. Even if the processor is slow, it does do well with the main user.

Yesterday I booted my desktop into the kids username, it was slow frame rate playing Supertux. I changed user to main, Supertux was good. Later I reboot into kids, and Supertux was fine. On my desktop it now appears to be a random problem. 

Thanks

---

