---
title: "libopenal0 update error"
date: 2006-08-02
forum: Desktop Environments
---

### Post by mozkaynak on 2006-08-02
Hi,
i am using 6.06 LTS. When I try to run Update manager, after I enter my password it examines the system and then it gives the following message:


[https://mywebspace.wisc.edu/mozkaynak/web/Screenshot.png?uniq=-ua2sbj](https://mywebspace.wisc.edu/mozkaynak/web/Screenshot.png?uniq=-ua2sbj)


My questions are:
1) am I in trouble? is it a big problem?
2) How can I fix this problem.

---

### Post by Ramses de Norre on 2006-08-02
Run ```
sudo aptitude update && sudo aptitude dist-upgrade
```
It's nothing to worry about, some updates require the removal of some other packages or something like that and a regular update isn't allowed to do this, a dist-upgrade is.

---

