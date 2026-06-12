---
title: "problem updating"
date: 2006-05-12
forum: Desktop Environments
---

### Post by dcc on 2006-05-12
I have been running Ubuntu 5.10 on a second laptop for a couple months with no problems. I have accepted any updates as they were offered from icon in teh upper right toolbar. It is now telling me that 3 updates are available. When I click on the icon, and enter my password, I get the message below.

[I][B]Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.[/B][/I]

I get this even after rebooting, and going straight to the updates. I am running a default installation, except for updating Firefox, using a script from this forum. I have used differant distros of Linux for a while now without virus or spyware protection. Does this suggest that something has infected my system, or does this point more to a bug in the update manager? A reinstall would not be a problem, but I would like to know what is causing this.  Any suggestions?

---

### Post by Sendervictorius on 2006-05-13
That message usually comes up when you have synaptic running, and try to do an update at the same time. 

In your case, I would imagine you have had a power failure, or otherwise stopped your system without a proper closedown, and a lock file has not been cleared. (Possibly even just the system clock was wrongly set at one point?)

Perhaps someone will know how the apt locking mechanism works, and how to clear the lock?

EDIT: - later
I searched the foums, and found this post: [http://www.ubuntuforums.org/showthread.php?t=156673](http://www.ubuntuforums.org/showthread.php?t=156673)
It seems that this may fix the problem:

joe@deadmeat:~ $ cd /var/cache/apt/archives
joe@deadmeat:/var/cache/apt/archives $ sudo rm lock

Also the lock in /var/lib/dpkg/  maybe worth removing.

Anyway, after a clean boot, and before using apt or synaptic or the updater it should be safe to remove these lock files. They hold no data, and removing should cause no harm. Worth a shot

---

### Post by stoffe on 2006-05-21
[QUOTE=Sendervictorius]That message usually comes up when you have synaptic running, and try to do an update at the same time. 

In your case, I would imagine you have had a power failure, or otherwise stopped your system without a proper closedown, and a lock file has not been cleared. (Possibly even just the system clock was wrongly set at one point?)

Perhaps someone will know how the apt locking mechanism works, and how to clear the lock?

EDIT: - later
I searched the foums, and found this post: [http://www.ubuntuforums.org/showthread.php?t=156673](http://www.ubuntuforums.org/showthread.php?t=156673)
It seems that this may fix the problem:

joe@deadmeat:~ $ cd /var/cache/apt/archives
joe@deadmeat:/var/cache/apt/archives $ sudo rm lock

Also the lock in /var/lib/dpkg/  maybe worth removing.

Anyway, after a clean boot, and before using apt or synaptic or the updater it should be safe to remove these lock files. They hold no data, and removing should cause no harm. Worth a shot[/QUOTE]
Thanks, removing both locks did the trick for me.

---

