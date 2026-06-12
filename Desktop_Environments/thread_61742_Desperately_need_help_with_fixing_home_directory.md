---
title: "Desperately need help with fixing home directory"
date: 2005-09-01
forum: Desktop Environments
---

### Post by neoprodigy on 2005-09-01
So I wanted to change the location of the my home directory to a mounted FAT32 partition.  So in the Users and Groups I changed the path to /media/home and then did killall gnome-panel to refresh my gnome bar.  After I did that everything disappared off my desktop including my gnome bars.  How can I set my home directory back to the original file path which was /home/user and get my desktop back which had my gnome panel. Thanks for any help, desperate n00b begging for help. :(

---

### Post by nad on 2005-09-02
If you have another user set up on your system, you may log in as that user and use the control panel to reset your ~/ location. I assume that you have not moved, or removed, any files yet.

Barring this, log in in recovery mode and edit the /etc/passwd file to your old home location.

This _may_ do the trick.

---

