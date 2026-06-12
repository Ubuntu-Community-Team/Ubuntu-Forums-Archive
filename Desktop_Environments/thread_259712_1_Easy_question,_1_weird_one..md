---
title: "1 Easy question, 1 weird one."
date: 2006-09-17
forum: Desktop Environments
---

### Post by Omegabf on 2006-09-17
The easy one:
I just adjusted my partitions to create a Fat32 for shared data.  I added the following to /etc/fstab
/dev/hda6    /media/files    auto    default    0    0
which connects the drive, but I only root gets rw access to it (I tried changing the option to rw,user but apparently that isn't right either).  How do I indicate that this drive should be available?


The weird one:
Every few boots, the welcome screen comes up in 640x480.  I can't see the user lists and clicking the options menu doesn't do anything.  (if I reboot at this point, it comes back up with the same problem)  I can still log in which brings up my desktop also at 640x480.  If I open the settings window, there is no option to switch to any other resolution.  If I reboot now everything goes back to normal.
I have moved to boot items around to ensure that I am not accidently entering recovery mode.
Any thoughts?

---

### Post by troughton on 2006-09-17
to get read wright access to the drive you need to alter it from root access to your access if you read the help files on [https://help.ubuntu.com/](https://help.ubuntu.com/) it will explane how i dont want to post it in the forums as you need to know what your doing to do becuase if you dont you can do more harm than good

---

### Post by Omnios on 2006-09-17
Years ago I had a lot of problems with my vfat My Docuements / Documents drive. I came up with this solution. Also there is a really good web page in my signature about fstab.

```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

```

---

### Post by Omegabf on 2006-09-18
Thankyou, I'll give that a try.

---

