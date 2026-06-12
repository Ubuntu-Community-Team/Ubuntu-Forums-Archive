---
title: "visualization in totem not hardware accelerated"
date: 2005-06-05
forum: Desktop Environments
---

### Post by mofojones on 2005-06-05
When I play a song in totem, the visualizations aren't using hardware rendering.  The framerates are abysmal, and forget about moving the totem window and rendering at the same time.

It's not mission critical, but it does affect the overall coolness of the desktop environment.  Any hints as to what to do?

BTW, I'm using a geforce mx4000 and the official nvidia drivers, and have verified that they work.

---

### Post by flanker on 2005-06-06
you can run the following from a terminal to see if direct rendering is enabled;

glxinfo | grep rendering


should return yes if its all OK.

---

