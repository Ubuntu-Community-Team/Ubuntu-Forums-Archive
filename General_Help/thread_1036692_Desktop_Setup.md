---
title: "Desktop Setup"
date: 2009-01-11
forum: General Help
---

### Post by untappedpilot2 on 2009-01-11
I'm running Xubuntu 8.10 and recently I've been thinking about clearing the hard drive and doing a fresh install. First I was wondering how I would go about formatting my hard drive? In my previous Ubuntu installs I was using Wubi (dual-booting with XP) and when I wanted to re-do my installation I would just go to "Add-Remove Programs" and uninstall it. Now I'm using the real deal and don't know how to go about it. Second, I've setup my desktop with a huge string of app-launchers that goes across the top panel. Is there a desktop file that stores this information I could save and push to the fresh install? (Once all the necessary programs were installed first.) 

-Thanks in advance!
Derek

---

### Post by Elfy on 2009-01-11
When you reinstall you can use the manual option - once in there pick the exisitng partitions and reuse them - tick the format box and it will format before it installs.

Your launchers are in your Desktop in /home - if you have a seperate /home then only mount it as /home do not format and it will still be there.

If you don't have a seperate /home then you can make one - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you don't want to make one then backup /home before you reinstall.

---

