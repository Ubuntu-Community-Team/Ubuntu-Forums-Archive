---
title: "breezy apt-get update killed my X and eth0"
date: 2005-12-06
forum: Desktop Environments
---

### Post by pinguskahn on 2005-12-06
I did an apt-get upgrade last week which led to a slew of errors and package dependency problems. The solution was to apt-get dist-upgrade but nothing was fixed. I manually removed the offending package which was at but now I can'tget X to fire up. The error given is "could not open default font 'fixed'". I have read through the forums and tried dpkg-reconfigure, symlinking font dirs, and even resintalling packages. Does anyone have any ideas on what I can do to fix this? 
My eth0 also doesn't start but I am less concerned about that since I can manually start it.

---

### Post by aysiu on 2005-12-10
Back up your data and do a clean reinstall?
Maybe make a separate /home partition so that next time you upgrade you can do a relatively painless reinstall.

---

