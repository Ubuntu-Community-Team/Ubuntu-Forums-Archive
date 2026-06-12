---
title: "Update and synaptic error"
date: 2009-03-04
forum: General Help
---

### Post by agentmulder on 2009-03-04
Hey, I woke up the reboot of my computer with a red round symbol with a white line through it. Tells me an error occurred to please run package manager.

This is the error I get in package manager:

E: Type '--2009-03-01' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read
Go To the Repository dialogue to correct the problem.
E: _cache->open() failed, please report.

What do I do? sorry for being a ubuntu noob.

---

### Post by taurus on 2009-03-04
Did you try to add Medibuntu to your repos?  There is something wrong with it.

```
cat /etc/apt/sources.list.d/medibuntu.list
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by agentmulder on 2009-03-04
Thank you, that linked worked. I was following some other guys codes to get medibuntu to work, and it just didn't.

---

