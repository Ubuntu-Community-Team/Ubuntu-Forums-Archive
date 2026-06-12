---
title: "Gnome login window scrolls"
date: 2006-09-16
forum: Desktop Environments
---

### Post by xtreme- on 2006-09-16
Hi,
I just bought a new LCD monitor, and started using the resolution 1600x1200.
I have a ATI Radeon 9800 Pro, and hence the newest fglrx drivers installed and configured (if that should matter).

My problem is that the resolution seems to be low in the GNOME login window: I only see a part of it on the monitor, and need to move the mouse to the edge of it to scroll it so I can find the box where I type my username.

But as soon as I type my user / pass and log in, everything is smooth (the resolution seems to get higher).

Any ideas on this one?
Thank you.

------
Edit:
Found some other threads on simular issues, and they referred to editing the resolutions found in Xorg.conf. So I left only 1600x1200 here, like this:
...
...
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1600x1200"
        EndSubSection
...
...

And now it works great:)

---

