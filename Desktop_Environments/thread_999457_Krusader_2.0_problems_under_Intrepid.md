---
title: "Krusader 2.0 problems under Intrepid"
date: 2008-12-01
forum: Desktop Environments
---

### Post by Godlikearg on 2008-12-01
Hi everybody,

I've been using Ubuntu Hardy on my laptop for a few months now, and recently I upgraded to Intrepid. I was also using krusader (1.90 I guess) and it got updated to 2.0. However, I noticed some problems which are starting to get annoying.

First, I have a /etc/fstab file configured to let me mount (well, not only me but any user in the system) some samba shares at home. It indeed works from the command line. But if krusader wants to enter a directory which hasn't been mounted yet, it fails with the message "mount: only root can do that". It was working perfectly on Hardy, even with Krusader's auto-mount feature.

I've been googling around for that but I couldn't find a solution for the problem. I even installed kdebase but that didn't fix anything.

The second problem I have comes when I try to umount ANYTHING, and I believe this is a slip from some dev (I'm no dev but given the error message, I think you'll understand :P). Anyway, the error message when trying to umount say, the directory /mnt/tanya/hd, is 

"Could not unmount device.
The reported error was:
sh: /bin/umount/mnt/tanya/hd: not found"

Krusader info:
Version 2.0.0-beta2 "SVN TRUNK Space Odyssey"
Using KDE 4.1.2 (KDE 4.1.2)

Any ideas about this?

Thanks in advance!

---

