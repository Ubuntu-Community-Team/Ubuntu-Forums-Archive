---
title: "gnome-settings-daemon takes up too much memory"
date: 2008-11-06
forum: Desktop Environments
---

### Post by yochaigal on 2008-11-06
Hello.

After upgrading to intrepid, everything worked just fine. Then I did some more updates (two days ago) and after rebooting, gnome-settings-daemon eats up 60 MB or so of memory!  I close it, and the usage drops to normal (of course, metacity gets all weird).

I cannot find any info on this problem online, nor can I find the answer in the forums.  Finally, there is nothing in the logs.

Any ideas? Directions?  Thanks!

---

### Post by smurfmatic on 2008-11-08
Yes, the same is happening to me. I've been with Intrepid since the alpha, and I have not noticed this memory problem until the release. It appears that gnome-settings-daemon is taking as much as 20% of 2Gb of memory.

Once, I left my computer on, went for a walk, came back just to find Gnome slowing down to a halt, with all the system memory being used up...

---

### Post by wedderburn on 2008-11-09
got the same issue, mine had a memory leak that went up 1.2gig

and currently its sitting at ~90mb, it was around 80 when i started this post.

---

### Post by szr4321 on 2008-11-09
I've found the following bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/293318](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/293318)

As described in the bug report, it also helped for me to remove the "wacom" sections and links from the xorg.conf. Apparently a fix should come soon, but it's a good workaround for now.

---

