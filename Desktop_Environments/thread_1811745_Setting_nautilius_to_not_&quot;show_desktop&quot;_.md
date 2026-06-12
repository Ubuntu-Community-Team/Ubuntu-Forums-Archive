---
title: "Setting nautilius to not &quot;show desktop&quot; prevents USB media from automounting! Help!"
date: 2011-07-25
forum: Desktop Environments
---

### Post by cwhittier on 2011-07-25
Is there a way to get removable media to automount to the /media folder when the "show desktop" option in nautilus is not checked? I've been trying to get this figured out for days!

---

### Post by cwhittier on 2011-07-26
After no replies here, and further research, I found a solution that worked for me, however it was slightly complex.

The problem lies in nautilus ending it's process because it sees there are no windows to be drawn. This means that USB drive insertion will not be detected.

The solution I used can be found here. It involves creating scripts and rules, and using udev to the detection and mounting. If you are just having trouble getting automount to work, and you have not intentionally stopped nautilus from running, this is probably NOT the solution to your issue.

[http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us](http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us)

---

