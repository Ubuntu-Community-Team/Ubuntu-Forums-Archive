---
title: "Offline KPPP installation -- will this work?"
date: 2009-05-18
forum: General Help
---

### Post by fredbird67 on 2009-05-18
I recently installed Ubuntu Jaunty Jackalope on an older computer and gave it to my father-in-law.  However, for some reason, he cannot connect to the Internet with GNOME-PPP (he lives out in the sticks, where all he has access to is a dialup connection), which I installed on there.

Therefore, I need KPPP instead.  As for getting it installed offline, is it possible to take KPPP and all its dependencies (which I already have on my flash drive), copy them into /var/cache/apt/archives/, and then run "sudo apt-get install kppp"?

The reason I say this is because I've observed that if a program you wish to install is already in the cache and you issue such a command (or click "Apply" in Synaptic"), that it doesn't download it at all and instead directly jumps to the installation step.  Therefore, I was wondering if this is possible.  I'm at work right now on a Windows machine (not my choice) and don't have access to a computer running Ubuntu to test this on right now.

Anyways, if this will work, I think, I hope, I pray, I might have a solution...

Thanx in advance,
Fred in St. Louis, MO USA

---

### Post by mac9416 on 2009-05-18
fredbird67, first of all, you can use [Keryx]("http://keryxproject.org") to get the dependencies. After you have all the debs you cna just double-click install each one. About the /var/cache/apt/archives/ idea, Keryx will probably be using that strategy for installation in its next release. However, I don't fully understand how it works, so I'll refer you to excid3 who does. You can find him on the #keryx IRC channel or on the [Keryx forums]("http://keryxproject.org/forums"). 
Hope that helps!
-mac

---

### Post by EXCiD3 on 2009-05-18
Copying the files downloaded elsewhere to the package cache will in fact work. You can also do this with the latest package lists and save them into /var/lib/apt/lists and run apt-get update to update the package list offline as well. I think I will be doing this for installation on Keryx as well as providing a local repository method of installation that would add an entry to the local sources.list for installation.

From St. Louis eh? I'm from Jacksonville, IL but go to school down at SIU Edwardsville nearby St. Louis. :D Nice to see fellow linux users in the area.

---

