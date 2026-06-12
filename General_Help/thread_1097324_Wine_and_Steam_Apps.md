---
title: "Wine and Steam Apps"
date: 2009-03-15
forum: General Help
---

### Post by mark.rogers on 2009-03-15
I know there are many tricks and tips on this subject, but so far I haven't found an answer to my problem. I'm trying to get CS:Source and/or Team Fortress 2 to run in Ubuntu. Apparently for most people it "just works", but for me, no dice. Here's my hardware:

Intel Core 2 Duo 2.2GHZ
3G of RAM
GeForce 9500M GS 

OS: Ubuntu Intrepid 64bit

I've tried the following driver branches:
173
177
180

All three seem to give the same results. In a perfect world, I'd like to stay with the 173.XX drivers, because the other seem to cause apps like Konsole to not refresh properly. I like Konsole, and thanks to work have to use it just a *bit* more than games. If the other drivers were to work, I *might* be willing to use Terminal, but it's a stretch. :)

I'm currently running the following version of wine:

wine-1.1.17

Now, Steam installs fine, and I can install the various games with out any major issues. When it comes time to run the games though is where I experience annoy issues. The following always happens:

1. Valve Logo
2. Source logo
3. Game's main menu background appears (without the background)
4. Game crashes with one of the following errors:
   a. Just "disappears", no errors
   b. failed to lock vertex buffer CMeshDX8::LockVertexBuffer
   c. Registry in use by another process (this generally occurs instead of the game launching at all)

Things I've tried:
Setting heapsize
Setting width/height
Setting dxlevel
Mixing the above with different drivers

Any thoughts out there? Really don't want to have to dual boot this laptop. Thanks in advance for any assistance, and sorry for what looks like a repost, but I swear I have dug through a myriad of other forum posts and such.

---

### Post by mark.rogers on 2009-03-16
bump..

---

### Post by zeusfaber on 2009-04-04
Mark, I am having the same issue with attempting to play Team Fortress 2. Anyone have an idea?

---

### Post by zeusfaber on 2009-04-04
The issue for me as gone away *mostly* by adding "-dxlevel 80" to the launch options (right click and properties) of a specific game.

---

