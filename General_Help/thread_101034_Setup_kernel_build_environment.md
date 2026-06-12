---
title: "Setup kernel build environment"
date: 2005-12-08
forum: General Help
---

### Post by mherring on 2005-12-08
Followed (or attempted to follow) instructions at this site...

[https://wiki.ubuntu.com/KernelHowto?highlight=%28build-essential%29#head-b15773fc5cb4997a033569b0f22c5452e538a45d](https://wiki.ubuntu.com/KernelHowto?highlight=%28build-essential%29#head-b15773fc5cb4997a033569b0f22c5452e538a45d)

The instructions call for installing as <user>, setting up as a member of the src group---and then upacking as <user>.

I could not make any of this work---and finally did everything as root (as I would have  if I had not read these instructions).

After this experience I suspect that some key step has been left out of the instructions on the wiki.

---

### Post by RAOF on 2005-12-08
All I can say is "that part worked fine for me".  But I was using that howto only as a guide, so it is possible that there is some important step left out.

Although I'd suspect that you didn't re-login after adding yourself to the "src" group.  That sort of change only applies to new logins.

---

### Post by mherring on 2005-12-08
One thing to add---since it all works fine as root, why do it any other way?

---

### Post by RAOF on 2005-12-08
Because it works fine **not** as root.  Why use the chainsaw when the pair of safety-scissors work?

---

