---
title: "Installing nvidia drivers Dell XPS17"
date: 2011-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LasseNC on 2011-12-28
Hello! 

I have a fresh Ubuntu install.

My problem is that when I enter the nvidia config, it states that I am not using the nvidia driver, but the additional drivers menu tells me its installed and activated.

When I do an lsmod in terminal, it says i915 at in the "video" line.

So how do I activate the nvidia drivers?

Kind regards, Lasse

---

### Post by senca on 2011-12-29
XPS generally uses the optimus technology with the consequence that the actual NVidia GPU will run idle in the background but cannot work with ubuntu. 
Perhaps that could be the problem?

---

### Post by LasseNC on 2011-12-29
> **senca said:**
> XPS generally uses the optimus technology with the consequence that the actual NVidia GPU will run idle in the background but cannot work with ubuntu. 
Perhaps that could be the problem?

I am not sure, but it could be.

In the meantime I've tried Fedora and Linux Mint with same results.

I think I read something about disabling optimus in the BIOS, but is that an advised thing to do?

---

### Post by n_u on 2011-12-29
Just checked my bios (l702x), but there isnt a possibility to disable optimus in the bios. It sounded strange to me, optimus is quite hackisch hardware crap, so disable @ bios would be strange lol.

---

