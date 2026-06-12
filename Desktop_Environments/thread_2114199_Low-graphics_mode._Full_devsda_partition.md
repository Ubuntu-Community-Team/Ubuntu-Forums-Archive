---
title: "Low-graphics mode. Full /dev/sda partition"
date: 2013-02-09
forum: Desktop Environments
---

### Post by boo2060 on 2013-02-09
Dear ubuntuforum users,

I get the "The system is running in low-graphics mode" error.

**Before the error** occured I (stupidly) messed around with permission in the *tmp* folder: I opened Nautilus (with root rights) and set the permission so that all processes are allowed to write to that folder.

After the reboot the system now displays the error message. I opened a terminal, logged in, and tried to **analyse the error**:

```
df -h
```reveals that my /dev/sda6 partition is almost completetly full:
> Filesystem: /dev/sda6 Size: 7.4G Used: 7.1G Avail: 0 Use%: 100% Mounted on /Another suggestion was to run
```
sudo du -kxa / | sort -nr | head
```with the result of
> sort: write failed: /tmp/sort[6 random letters, e.g. SFyDay]: No space left on device.I read that full disc space may result in this error so I guess that a process (after I changed permissions) filled my *tmp* folder. I am not able to enter any graphical interface, only have the terminal. I am not a really advanced user so please bear with me. My questions are: How do I navigate to that full *tmp* folder and delete content? And how do I set the permissions to the previous state?

---

