---
title: "Video Drivers On Server"
date: 2008-12-22
forum: General Help
---

### Post by dethredic on 2008-12-22
So, I am running a small personal 7.1 server with kbuntu.

Yesterday my computer died, and I have a project to do, so I am forced to use  my server. Anyways when I am in x there is a bad resolution and some ghosting so getting some drivers would be nice.

I go to the restricted server manager and it says:

You need to install the package
linux-restricted-modules-2.6.22-16-server
for this package to work

I head over to synaptic, but there is no such package there.

---

### Post by Titan8990 on 2008-12-22
That is because it is actually not supported on the server kernels. Servers are meant to run headless.

The best you can do is find out your graphics card with lspci -v.


Then try to select the best possible option from the following command:


sudo dpkg-reconfigure xserver-xorg


or you can manually edit xorg.conf if you feel up to it.

---

### Post by dethredic on 2008-12-22
Shucks.

I reconfigured x but that didn't help

---

### Post by Titan8990 on 2008-12-22
Did you switch from vesa drivers to ones that match your hardware?

---

### Post by dethredic on 2008-12-22
I don't entirely understand what you mean.

When I went through the reconfigure, it detected my hardware correctly.

---

