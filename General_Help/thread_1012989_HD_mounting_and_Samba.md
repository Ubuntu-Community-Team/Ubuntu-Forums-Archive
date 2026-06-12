---
title: "HD mounting and Samba"
date: 2008-12-16
forum: General Help
---

### Post by adlin5000 on 2008-12-16
Well it seems like I have a few issues that have popped up recently. Please bear with me as this might take a while.

First off I upgraded from 8.04 to 8.10 using the update manager. This broke some things, but only required the reinstall of some that we either lost in the update or were still installed but showed as not through synaptic.

The biggest problem was my samba shares vanished. Even I could not access them. (I could still access the files, just not through the network).

Then I tried a fresh 8.10 install. After the install I discovered that I now have to manually mount my other HD's each time I restart. Also after a little looking around the forums I found out that there is now issues with Samba in 8.10.

Now I have done a fresh install of 8.04 in the hopes that I could just go back to the way it was. Unfortunately I still have to mount the HD's each time and Samba still won't work.

Any help? At this point I'm getting very frustrated. Let me know if any more info will help.

Thanks

---

### Post by cariboo on 2008-12-16
Because you did a clean install, you will have to edit /etc/fstab to automount your drives, and you will have to edit /etc/samba/smb.conf to get your shares to show up. Do you have backups of either file?

Jim

---

### Post by adlin5000 on 2008-12-17
I do, but fstab will probably have changed. I had to make a new partition to install on so I would not loose 200gb of data. With all my previous installs the drives were automatically detected and mounted at hda#/hdb#/sda#/sdb#. Whats changed that I have to do differently now?

---

