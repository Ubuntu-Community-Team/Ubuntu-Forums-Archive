---
title: "Left Mouse Button stops working on Ubuntu 14.04 LTS"
date: 2015-11-20
forum: Desktop Environments
---

### Post by KJKJKJ on 2015-11-20
BACKGROUND

There are already several threads on this but quite old, and few fixes.

PROBLEM

The left mouse button stops working but the right mouse button still works, not fixed by logging out and back in again, or reboot.
 
A telltale sign is that it is confined to the user; for example login as guest and everything works.
Another sign is that if you use Synergy, it works on other machines.

It just happened to me and it's** horrible**, but I fixed it, and was so grateful to the fates I signed up to this forum to share.

SOLUTION

If you can get the mouse left button to work by holding down either of the Win / Super keys (don't ask how I discovered that) then fire up 'Tweak Tool' (the Gnome one, not the Unity one) and choose *Windows | Windows Action Key* and then chose *Super* in the drop down menu. Beforehand, mine was set to *Disabled*. This is indeed counter-intuitive.

Hope this helps.

---

