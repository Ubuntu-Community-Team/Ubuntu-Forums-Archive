---
title: "Proprietary ATI drivers - show up on live cd but not on install (ATI Mobility HD4570)"
date: 2009-05-13
forum: General Help
---

### Post by stwschool on 2009-05-13
As per the text. Any ideas guys? I'd like the drivers so I can use compiz, it helps my workflow with stuff like expo, I'd hate to do without it.

[EDIT: PS I tried installing the flgrx driver from synaptic and the screen was badly corrupted on restart so that's probably not a good sign]

---

### Post by UJM on 2009-05-13
I'm using an ati 4870 card and just downloaded the latest Catalyst (v9.4) driver from the ati website then followed the instructions in their pdf guide, worked fine and you get the latest driver.

---

### Post by stwschool on 2009-05-13
Cheers, I'll give it a try. As an alternative just in case, would tricking jockey into supporting my card by modifying /usr/share/jockey/modaliases/fglrx-modules.alias.override be effective?

---

### Post by Legace on 2009-05-13
Never use the restricted manager. I **always** have gotten some sort of problem (black screen, flickers, very low res, etc.) when using it..

Use either the ATi documentation or wiki.cchtml.com :)

---

### Post by stwschool on 2009-05-13
Really? I've used jockey before very successfully on my recently departed old laptop (Ati, only good for 8.10) and my desktop with a lovely NVIDIA driver.

---

### Post by stwschool on 2009-05-13
Just a quickie to say I think I've solved the problem. I had forgotten to do what I usually do which is switch away from the Thai repository as soon as possible. Sadly the Thai repository is mostly non-functional and so presumably nothing registered when it was queried for a driver. Switching to the US one has brought back the option of proprietary graphics drivers so one can only assume the problem is solved. I'll have a go tomorrow at school where my net's a bit faster as it seems to be crapping out on my slow net (some visual feedback when using jockey would be nice, the progress bar is just a lie).

---

