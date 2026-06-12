---
title: "New user created has no sound on Gateway laptop"
date: 2006-02-04
forum: Desktop Environments
---

### Post by Hunkadoodledoo on 2006-02-04
So, I installed Kubuntu 5.10 on a Gateway work laptop pretty much to use to play CDs in the background while we work, and I created a user "josh" when I installed and another user "WORK" inside KDE.  When I login as josh, I get the start up sound and CDs play fine.  When I login as WORK, I get an error about the sound something like this:

device /dev/dsp can't be opened (No such file or directory)

and the sound doesn't work.

Why would it work for one user and not another?  I looked around, but I couldn't troubleshoot it too much - I had other work to do.  Any help is greatly appreciated!

---

### Post by Sutekh on 2006-02-04
How did you create the new user?  Through the command **adduser** or through the **Users and Groups** GUI (in the System -> Administration Menu)?

The cause of this problem is most probably to due with the groups that the user WORK belongs to.

Check out this
```

user@ubuntu:~$ ls -l /dev/dsp
crw-rw----  1 **root** **audio** 14, 3 2006-02-05 15:25 /dev/dsp
user@ubuntu:~$

```
This means that the sound device /dev/dsp is owned by the user **root** and the group **audio**.  Both root and the group audio have read/write permissions to the device.  So to use it you either have to be the user root or in the audio group.

You can check using the command line if the new user (WORK) is in the audio group.
```
groups WORK
```
This will return a list of groups that WORK belongs to.

To add WORK to the **audio** group, use the command
```
sudo adduser WORK **audio**
```

To use the GUI method, open the **User and Groups** GUI and choose WORK and click **Properties**.  Then choose **User Privileges** and make sure the **use audio devices** box is checked.

That should set you up.

---

