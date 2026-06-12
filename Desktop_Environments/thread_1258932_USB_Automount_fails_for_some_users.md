---
title: "USB Automount fails for some users"
date: 2009-09-05
forum: Desktop Environments
---

### Post by RayDeCampo on 2009-09-05
I have an unusual problem where USB automount succeeds for some users but fails for others.  All users have all available permissions granted via the GUI tool.  This is a clean 9.04 install with all updates applied.  Some files for /home were copied from an old 9.04 installation (which had been upgraded incrementally from 7.10).  When the good is logged in and I stick in the USB stick, it automounts and the nautilus windows pops as expected.  When I try the same thing (same port and USB stick) with the bad user, the USB stick blinks a couple of times and nothing happens.

I would appreciate any guidance.

---

### Post by Petertje on 2009-09-05
does this happen with same users every time or random user?

---

### Post by RayDeCampo on 2009-09-05
> **Petertje said:**
> does this happen with same users every time or random user?

Same users every time.  Good user can consistently automount USB drives, bad user consistently cannot.

---

### Post by RayDeCampo on 2009-09-11
Of course now the computer wants to make a liar out of me, and the good user cannot mount the USB stick as well.  I'd appreciate any guidance, I haven't found anything in the logs.

---

### Post by Petertje on 2009-09-24
Have you checked if the good users and bad users are in the same group? If not - there's your answer :)

else..
If you create a new user, will it have the same problem with mounting or will be fine?
If it is fine try to delete literally everything from bad users (settings) and re-make them to check whether it is ok.

If that doesn't work i am out of ideas for now :P

good luck

---

