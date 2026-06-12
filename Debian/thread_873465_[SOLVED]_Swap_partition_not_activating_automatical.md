---
title: "[SOLVED] Swap partition not activating automatically"
date: 2008-07-29
forum: Debian
---

### Post by p_quarles on 2008-07-29
I recently installed Sidux on an older laptop (specs follow), and partitioned the drive manually. At first, everything was working correctly. After trying and failing to hibernate a session, the swap partition no longer gets activated during bootup. In order to use it, I have to run mkswap and swapon each time. 

The line in /etc/fstab is like so:
```
UUID=4bd062b1-a45d-4f6a-a308-2b4baa8197dd       none    swap    sw      0       0
```
Basically, I don't get why it isn't working, as this line looks exactly like every other swap mount line I've seen. Any further insights into the process behind automounting a swap file?

The laptop is a Dell Dimension 8000, Pentium 3 (800 MHz), 384 MB of RAM (so it needs a swap file).

---

### Post by Arthur Archnix on 2008-07-29
After a clean boot, what's the output of swapon -s? Also, I experienced some similar weirdness once, but there was an error in my boot log about unable to start swap. Are you seeing that as well?

If you're description of the events leading up to the problem is correct, I'd guess that you've got a lockfile laying around somewhere that is telling the system it's not safe to bring up the swap space. Two ways around that would be to:

1) Find this theoretical lockfile and vaporize
2) Unmount, re-format partition, give new UUID and update fstab | delete, recreate then update fstab

Option 2 is how I solved my problem.

Lastly, not directly related to solving your problem, but perhaps of interest to you in avoiding it:

[http://www.debian-administration.org/articles/550](http://www.debian-administration.org/articles/550) 

I don't hibernate my system because it's faster for me to shut it down and power it on, so I can't offer much in the way of guidance for your hibernate issues. Running dpkg-reconfigure uswsusp (which is the package I think is handling s2ram and s2disk) will let you reconfigure the logging verbosity, which may help you in diagnosing what's going wrong.

---

### Post by odiseo77 on 2008-07-29
Have you tried executing: ***vol_id -u /dev/YOUR_SWAP_DEVICE*** (as root) to see if the output matches the UUID of the one shown on your /etc/fstab ? (I had a similar problem once on Ubuntu and that's how I solved it).

---

### Post by p_quarles on 2008-07-29
> **odiseo77 said:**
> Have you tried executing: ***vol_id -u /dev/YOUR_SWAP_DEVICE*** (as root) to see if the output matches the UUID of the one shown on your /etc/fstab ? (I had a similar problem once on Ubuntu and that's how I solved it).
I just did that, in fact, and think that might be the problem. The uuids did did not match. Another bootup will determine whether or not that was the issue, but at the moment I suspect it is. 

@Arthur: thanks for the link to the dynamic swap file deal. That's just cool enough that I'll have to try it regardless of anything else. :)

EDIT 7/30: Indeed, the altered uuid was the cause of the problem. Correcting the entry in fstab resolved the issue. Should have done that before posting. :)

---

