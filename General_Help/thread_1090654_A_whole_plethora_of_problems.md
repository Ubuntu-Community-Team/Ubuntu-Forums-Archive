---
title: "A whole plethora of problems"
date: 2009-03-08
forum: General Help
---

### Post by TJoh311 on 2009-03-08
Hello, 
I'm currently running 8.04 on my p4 ht machine. 32-bit kernel compiled smp.
Last night I installed some updates, and this morning my flashplugin for mozilla stopped working. While I was trying to troubleshoot that, Synaptic dissapeared from my administration menu. If I right-click>> edit menu, It shows it there but it won't let me check it. So where do I start? I want to try to go back to the way my machine was yesterday before the updates but I'm not sure how.

---

### Post by albinootje on 2009-03-08
> **TJoh311 said:**
> I want to try to go back to the way my machine was yesterday before the updates but I'm not sure how.

Can you perform the following in a terminal and post the output of possible errors ?
```

sudo apt-get update
sudo dpkg-configure -a
sudo apt-get -f install

```
After that, try this in a terminal, and see whether that's going well :
```

gksudo synaptic

```

---

