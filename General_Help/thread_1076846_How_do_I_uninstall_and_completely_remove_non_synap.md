---
title: "How do I uninstall and completely remove non synaptic package?"
date: 2009-02-21
forum: General Help
---

### Post by Rytron on 2009-02-21
Hi. I installed yabause-0.9.9.x86.package
There is an older version in Synaptic that I have not installed.
How do I uninstall and completely remove the yabause-0.9.9.x86.package?
Thanks.

---

### Post by heindsight on 2009-02-21
that depends on how you installed it. did you build from source or install from a .deb that you downloaded from somewhere?

---

### Post by Miaxi on 2009-02-21
sudo apt-get purge yabause* 

Check the filenames it offers to remove and confirm if those are correct.

---

### Post by snova on 2009-02-21
> **Rytron said:**
> Hi. I installed yabause-0.9.9.x86.package
There is an older version in Synaptic that I have not installed.
How do I uninstall and completely remove the yabause-0.9.9.x86.package?
Thanks.

Well, since it's an autopackage, try this:

```
package uninstall yabause
```

I'm not really sure, but it seems right.

---

### Post by Rytron on 2009-02-21
> **snova said:**
> Well, since it's an autopackage, try this:

```
package uninstall yabause
```

I'm not really sure, but it seems right.

Cheers snova. Just adding sudo to the start and all is done.

:popcorn:

---

### Post by fragos on 2009-02-22
Synaptic, Add/Remove, Ubuntu Tweak, dpkg, apt-get and aptitude all use the same package database for install and removal. A pckage installed with one method can be removed with another. Add/Remove and Ubuntu Tweak have less visibility of deb packages but their actions are still compatible with the others.

---

