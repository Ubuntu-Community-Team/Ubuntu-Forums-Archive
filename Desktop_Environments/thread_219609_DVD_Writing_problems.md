---
title: "DVD Writing problems"
date: 2006-07-20
forum: Desktop Environments
---

### Post by bleucanard on 2006-07-20
I am using Dapper and have the following problem with my DVD writer :

when I insert a blank DVD to write on, it automatically gets mounted
to /media/dvdrecorder, with access 766 (rwxr-xr-x) and owner root.
If I try to run growisofs (or apps like k9copy, k3b, etc...), it won't 
work unless I am logged in as root.

How can I change it so that it gets mounted with either access 777, or
myself as the owner (preferably the latter) ?

There is no entry for my DVD drive in fstab, and I couldn't find a rule in udev that mounts it automatically. Would it work to add an entry in fstab with the right uid and groupid, or would it conflict with whatever is automatically mounting the DVD drive into /media/dvdrecorder ?

Pierre

---

### Post by ColinG on 2006-07-20
Have you tied K3b Set-up under the Settings menu?

---

### Post by bleucanard on 2006-07-20
Thanks, the settings in k3b are the default one and seem ok.
My problem is not just with k3b though. It happens with growisofs,
k9copy, and even Totem when playing back some dvd's.
What I would like to do is change the default access rights and owner when the dvd is mounted, not when k3b or others are running, but I can't find
where this is done (and I looked for...oh... at least half a minute !)

---

