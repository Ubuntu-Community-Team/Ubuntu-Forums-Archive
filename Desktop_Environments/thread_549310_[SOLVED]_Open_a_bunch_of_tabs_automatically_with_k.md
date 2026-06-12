---
title: "[SOLVED] Open a bunch of tabs automatically with konsole"
date: 2007-09-12
forum: Desktop Environments
---

### Post by pat3691 on 2007-09-12
I have script starting konsole with several tabs opening automatically pointing to different hosts (using ssh).  

The problem is that it crashes after opening all the tabs (no matter what number of tabs).  After troubleshooting a bit, I found out that there are lines starting with Args that make it crash.  The whole point is to open the tabs pointing to different hosts using ssh and the ssh command must be in that line (Argsx=......)


Question: How can I fix that

---

