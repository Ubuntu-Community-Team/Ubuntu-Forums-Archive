---
title: "Kiba-Dock Physics Settings"
date: 2008-06-18
forum: Desktop Environments
---

### Post by mo0osah on 2008-06-18
I was playing with the physics engine in kiba-dock and I screwed up all the settings.  I was wondering if someone could post their values for Elasticity, K, Gravity, Friction, and Inertia values.  Thanks.

EDIT: I think I posted this in the wrong sub-forum.  Apologies for that.

---

### Post by NikoC on 2008-06-19
Hmmm, this is just a thought, but when you install applications such as Kiba they often create a hidden folder in your homedirectory in which they store there settings.

So if you are in a terminal, go to your home folder (cd ~/) and type ls -A. This will get you a list of all files and folders, including the hidden ones (these start with a .). Look for a folder containing kiba and then do:
sudo rm -r .foldername

Normally when you start Kiba now, it will be using its initial install settings.

Cheers.

---

