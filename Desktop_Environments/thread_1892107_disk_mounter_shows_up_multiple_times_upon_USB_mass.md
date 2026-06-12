---
title: "disk mounter shows up multiple times upon USB mass storage insertion"
date: 2011-12-07
forum: Desktop Environments
---

### Post by jayage on 2011-12-07
If I insert any mass storage in USB (e.g.; flash stick, iPhone) multiple Disk Mounter applets show up. Web searches don't bring up anything useful, unlike every time before.
It doesn't seem to be autofs, used for automounting NFS drives, because stopping the service doesn't solve the problem.

Running Natty, fully updated, with Gnome 2.32 ("Classic" session).

I'll post any relevant config files that might help in diagnosis, once you suggest where to start looking.

---

### Post by mohammadul on 2011-12-07
if u use any(autofs) auto mounting software at the boot-up, try reinstalling that... or may need to reset??

---

### Post by jayage on 2011-12-08
> **mohammadul said:**
> if u use any(autofs) auto mounting software at the boot-up, try reinstalling that... or may need to reset??

As mentioned above, I do use autofs. However, the problem persists after stopping autofs daemon.

Even though I was skeptical, autofs was reinstalled, but it didn't help. Reset? You don't mean restart, that's why we don't use windows anymore, right? ;) Jokes aside, the machine is restarted from time to time (kernel updates etc.). Again, it changes nothing.

Any more suggestions?

---

