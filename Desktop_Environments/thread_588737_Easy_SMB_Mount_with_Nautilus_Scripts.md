---
title: "Easy SMB Mount with Nautilus Scripts"
date: 2007-10-23
forum: Desktop Environments
---

### Post by ryanchew on 2007-10-23
Hey everyone,

I created some nautilus scripts to mount SMB shares and ISO/UDF files with a simple GUI interface using Zenity.
**Requirements:** zenity, smbfs (zenity should be included in a default Ubuntu installation)
**Installation:** Just pop them in your ~/.gnome2/nautilus-scripts folder and you should be able to use them. If you don't have smbfs, just run this command.
**Tested On:** Ubuntu 7.10

**Download:**
[http://ubuntustuff.chewablestudios.com/mount.sh](http://ubuntustuff.chewablestudios.com/mount.sh)
[http://ubuntustuff.chewablestudios.com/unmount.sh](http://ubuntustuff.chewablestudios.com/unmount.sh)

**How to use:**

```

**Instructions:**
*Mounting*
    * Right click on SMB folder or ISO/UDF file
    * Scripts -> mount.sh
    * Select mount point
    * Mount as read-only?
    * Type in SMB user name (SMB only)
    * Type in SMB password (SMB only)
    * You're done :)

*Unmounting*
    * Right click anywhere
    * Scripts -> unmount.sh (script scans for mounted smb and iso/udf files)
    * Select volumes to unmount
    * You're done :)

```Please do let me know if you encounter any problems or if you have any improvements/suggestions/feedback.

Thanks!

---

### Post by K.Mandla on 2007-10-26
Moved to Desktop Environments.

---

