---
title: "Linux Partition on USB stick"
date: 2010-06-10
forum: Desktop Environments
---

### Post by TheNewbieGeek on 2010-06-10
I formatted a partition on a USB stick in ext2 format for Linux with GParted. I tried to extract a file onto the partition and received a error that said I did not have the permissions to do it. thanks for the replies.

---

### Post by SlidingHorn on 2010-06-10
Going to need more info.  What's the file, what program are you extracting with, what method did you use to do so, what's the exact error (was it a dialog or were you doing this in a terminal?), etc...

---

### Post by TheNewbieGeek on 2010-06-10
> **SlidingHorn said:**
> Going to need more info.  What's the file, what program are you extracting with, what method did you use to do so, what's the exact error (was it a dialog or were you doing this in a terminal?), etc...

I am extracting a os onto a sd card. The program I am extracting with is called extract. The default one used with ubuntu. Here is the error:

You don't have the right permissions to extract archives in the folder "file:///media/fc18eacb-28dc-4300-a10c-f846e562d22d"

---

### Post by C.S.Cameron on 2010-06-10
Try an F2 and type "gksu nautilus".
This will open nautilus with root privileges.

---

### Post by TheNewbieGeek on 2010-06-10
Worked!! thank you.

---

