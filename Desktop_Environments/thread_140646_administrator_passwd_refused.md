---
title: "administrator passwd refused"
date: 2006-03-06
forum: Desktop Environments
---

### Post by walvirch on 2006-03-06
Installed Kubuntu in "expert" mode-set root passwd and install went ok.
However whenever a screen requires "administrator" the system won't buy my password "sorry su". Terminal mode for root (#) works on password  and I have all root priviledges.As the only user of a multiboot system(SUSE10.0 and windows xp installed) I don't know why I don't have addmin priviledges. Had the same problem with Ubuntu but can't remember how I fixed it.Did I miss an option somewhere?  Only one group and I it!

---

### Post by Mustard on 2006-03-06
I'm having a bit of trouble making sense of your post, but I can tell you that expert mode sets you up with a root password, but the first user account is not part of the admin group.  You would need to edit the /etc/sudoers file using the visudo command to either add your username to the sudoers file, or add your user to the admin group.  You have the root password, so it shouldn't be much of an issue doing the above.

---

### Post by walvirch on 2006-03-06
Thanks---I think that I fixed Ubuntu with sudo when I was configuring wvdial for my dialer.Will try the same with Kubuntu.

---

