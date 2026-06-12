---
title: "Synaptic Package Manager"
date: 2009-06-24
forum: General Help
---

### Post by MarkBM on 2009-06-24
Hello Forum Readers
I Have a problem opening SPM in 9.04. When I try to open it I get this message.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Any ideas how to resolve this would be much appreciated. Not sure how to deal with this in the terminal. I would say my system is way behind in updates. Right clicking the icon in the task bar (which is now & for sometime been a red filled circle with a white bar through it) fails to open the manager.

Cheers,

MarkBM

---

### Post by gettinoriginal on 2009-06-24
Cache open indicates that you have more than one application manager open.  check to make sure that terminal or add/remove applications are not open, then go to synaptic.  :P   If you are concerned with updates, then open a terminal and type
```
sudo apt-get update
```

---

### Post by Soul-Sing on 2009-06-24
gettinoriginal probl. you are right, when it is corrupt please:


```
sudo rm /var/lib/apt/lists/* -vf
```




```
sudo apt-get update
```

---

### Post by drs305 on 2009-06-24
Edit: too late, eloquant's got you covered.

I recently posted regarding a similar problem. Post #2 should fix it for you:
[http://ubuntuforums.org/showthread.php?t=1192817#2]("http://ubuntuforums.org/showthread.php?t=1192817#2")

---

### Post by MarkBM on 2009-06-27
Thanx leoquant, this has resolved the problem.

---

### Post by MarkBM on 2009-06-27
Thanx drs305, your screenshot is identical to what mine was showing.

---

