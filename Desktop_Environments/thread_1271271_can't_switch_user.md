---
title: "can't switch user"
date: 2009-09-20
forum: Desktop Environments
---

### Post by lovrenca on 2009-09-20
Hi.
In the two years since I have switched from windows to ubuntu, this is the first problem I am unable to solve even after spending more than 5 hours searching for the answer. The problem is the following:

After installing propertial (fglrx) driver for my ati hd 4890 graphic card I am unable to switch from one user to another.(not with the fast user switch applet and not with the button switch user in the locked csreen).
The screen goes black for a few seconds and than I land back where I was before the attempt to switch user(locked screen or desktop). When switching with fast user switch applet the result is:

[I]The graphical interface did not properly start, which is needed for graphical logins. It is likely that the X Window System or GDM is not properly configured.
The X server failed to finish starting.
3 X failed[/I]

and in the locked screen:
[I]Cannot start new display
The X server failed.  Perhaps it is not configured well.[/I]

I would appreciate any help, and if there is a thread with a similar problem, you belive might help, please paste a link.

---

### Post by lovrenca on 2009-09-23
Anyone?

---

### Post by lovrenca on 2009-09-25
bump

---

### Post by lovrenca on 2009-09-26
Please help guys, this is a problem.

---

### Post by lovrenca on 2009-09-28
So I guess a sollution for this problem does not exist...
In that case please close the topic.:guitar:

---

### Post by Minsky on 2009-09-28
I think the problem lies with the proprietary driver. I'm using a HD 4830 and I've got a similar problem to yours. I think the solution is to use open source drivers but with the drawback that you may not be able to enable extra visual effects

---

### Post by lovrenca on 2009-09-28
Yes as far as I have researched this problem I must agree with you, the drivers are definitelly at fault here. I have an ati radeon 4890 card and use the fglrx drivers. I tried reseting xorg settings with sudo dpkg-reconfigure xserver-xorg but it trashed my x session and had to repaire it in the root session-terminal... but that was after restart. when I tried switching user, after runing this command, it worked!(warning, do not use that command, had very bad experience with it :( )

---

