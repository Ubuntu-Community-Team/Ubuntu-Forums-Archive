---
title: "Unable to startx unless root does startx first"
date: 2017-03-09
forum: Desktop Environments
---

### Post by mvidberg on 2017-03-09
I have come across a very strange issue.  I recently upgraded from xubuntu 16.04 to 16.10 and it started coming up to a black screen at the point where the XFCE session normally loads.  So I logged in via single mode and changed to text only boot.  When I log in with my normal user account (via text console) and then type "startx", it still comes up as a black screen.  If I login with root first (yes, I enabled password on root account so i can login with it) and do "startx", xfce starts fine.  I can then switch to another console login prompt (via Ctrl-Alt-F2) and login as my normal user and do "startx" again.  This time it will work fine and load xfce with no issues.  Seems that regular users can no longer access display port 0, but root can.  Other users can then startx on display port 1.

Anybody have any idea how I can make display port 0 accessible to normal user again?

---

