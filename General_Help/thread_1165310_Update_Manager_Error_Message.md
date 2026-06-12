---
title: "Update Manager Error Message"
date: 2009-05-20
forum: General Help
---

### Post by jet.he.is on 2009-05-20
i've recently installed and uninstalled several packages, and after getting everything working, found a red circle with a dash through it in my notification area that has a tool tip 'A problem occured when checking for the updates.' I've googled the error and done apt-get updates, upgrades, and safe-upgrades, and none of these actions caused any errors or resolved the issue. maybe i'm missing where this error is coming from? also, restarting the computer doesn't cause the error to go away.

thanks in advance

---

### Post by ActiveFrost on 2009-05-20
Have you tried to change your default servers ( System -> Administration -> Software sources ) ?

---

### Post by jet.he.is on 2009-05-20
> **ActiveFrost said:**
> Have you tried to change your default servers ( System -> Administration -> Software sources ) ?

My school hosts a mirror of the ubuntu repositories, so i use those, but i haven't touched sources.list or software sources in weeks, and there's no problem with the school repos.

---

### Post by paradigm2 on 2009-05-20
It does not give any more info with the error message?

---

### Post by jet.he.is on 2009-05-20
> **paradigm2 said:**
> It does not give any more info with the error message?

no, and that's why i really don't know where to go from here.

---

### Post by jet.he.is on 2009-05-21
figured it out. during my previous installs, i switched to python 2.4 to get plone working. apparently update manager relies on python 2.5 or 2.6 libraries, which is what caused it to behave strangely.

---

### Post by tkearn5000 on 2009-12-08
Just wanted to thank you. Your post helped me solve this problem. After trying a number of things, I came across your post, and at the mention of python realized I had installed a new version, and changed the python link in my /usr/bin to link to python3.1. Changing it back to 2.6 solved the problem right away. I would never have thought of that on my own.

Thanks again,
-Tim K

---

