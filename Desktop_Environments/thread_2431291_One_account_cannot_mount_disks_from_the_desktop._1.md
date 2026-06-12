---
title: "One account cannot mount disks from the desktop. 18.04"
date: 2019-11-14
forum: Desktop Environments
---

### Post by ubuntone on 2019-11-14
My install account has stopped mounting disks and usb sticks from the desktop.

I get a window with titled Mount Failed
Failed to mount "sandisk"
Not authorized to perform operation

Another account with (I believe) the same privileges has no problems.

I can't see why.

Suggestions welcomed on where to look and what has changed.

Thanks

---

### Post by TheFu on 2019-11-14
Check the group memberships for each userid. Compare user1 with user2.  What's different?

---

### Post by ubuntone on 2019-11-14
will is the install account that is failing

rob is the account that works

> will@trebor2:~$ groups
will adm cdrom sudo dip plugdev lpadmin sambashare chrome-remote-desktop


> rob@trebor2:~$ groups
rob adm cdrom sudo dip plugdev lpadmin sambashare


---

### Post by ubuntone on 2019-11-14
removal of the group "chrome-remote-desktop" allows it to work after a reboot.

re adding  the group "chrome-remote-desktop" stops it to working after a reboot.

---

### Post by ubuntone on 2019-11-14
I have same system installed on a memory stick

This performed the mounts before upgrade.

After upgrade to the latest updates it is stopping the mounts,

Any idea what about chrome-remote-desktop is stopping the mounts working?

---

### Post by TheFu on 2019-11-14
I suspect it has less to do with chrome-remote-desktop and more to do with who is physically running the login session under the plugdev group.

For decades, mounting storage was restricted to admin users only with end-users not allowed to perform that operation.  There are settings that can be added to the fstab or autofs configs which can allow users to mount storage.

As for allowing automatic mounting, I don't know anything about it. My servers don't allow that.

---

### Post by ubuntone on 2019-11-14
I have asked a question on Google Support Forum to see if they can advise..

[https://support.google.com/chrome/thread/19869799?hl=en](https://support.google.com/chrome/thread/19869799?hl=en)

---

