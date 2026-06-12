---
title: "VNC server doesn't show desktop"
date: 2009-05-22
forum: General Help
---

### Post by renkinjutsu on 2009-05-22
i am able to connect to my ubuntu box using vinagre, but the problem is that when i connect, i can see the screen but vinagre is always stuck on the first frame (but the cursor moves and i'm able to launch things) i can click on launchers on vinagre but the screen doesn't change (again, it shows the cursor moving) but when i get back onto the host computer, i see all the applications i launched using vinagre.. what's wrong? is this a problem with X?

i'm hosting the server with Vino, and i have the boxes checked to enable users to view and control the desktop

---

### Post by XCan on 2009-05-22
This is a known and realy annoying bug. It appears to be a compiz problem. Somehow, the screen doesn't know it's 'damaged' and thus won't send the 'damaged' parts for refresh. It is possible to circumvent this in two ways currently:

1) Disable Desktop Effects (compiz)
2) Use a vnc server supporting -noxdamage flag

The first option is straight forward. The second option can be achived by installing another server or using the patch as discussed in [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126) .

---

