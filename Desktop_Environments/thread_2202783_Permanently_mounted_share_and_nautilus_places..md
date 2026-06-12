---
title: "Permanently mounted share and nautilus places."
date: 2014-01-31
forum: Desktop Environments
---

### Post by Prunkdump on 2014-01-31
Hello,

I have two mounts that need to be accessible to all my users :
-> a cifs mount on an external server 
-> a ext4 mount on a local drive partition

I want there mounts appear on the nautilus "places" menu automatically.

1) If I mount them in the "/mnt" folder there does not appear in Nautilus.
2) If I mount then in the "/media" folder there appear in the nautilus "devices" but with a "umountable" icon like a flash drive. But I don't whant my users thinks they can umount there shares.

Is there a way to make the mount appear as a "static" mount in the nautilus "places" ?

The cifs share is mounted with pam_mount (it need the user password). Is there a way the "places" icon is created automatically when the share is mounted ?

Thank you.

Baptiste.

---

