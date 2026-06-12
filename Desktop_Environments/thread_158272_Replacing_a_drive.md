---
title: "Replacing a drive"
date: 2006-04-10
forum: Desktop Environments
---

### Post by qwert231 on 2006-04-10
I have 3 drives on my system. One is root (\), one I have as \var, and one I call \fileshare, which I've been using for network storage. But I've filled it up. I want to replace it with a larger drive. What's the easiest way to move the whole \fileshare partition to the new drive.

(With the 3 disks and one CD-Rom, I don't have any more IDE channels.)

---

### Post by taurus on 2006-04-10
Archive the /fileshare (not \fileshare) and back it up on a DVD or something (or to another partition.  Remove the old drive and install the new one.  Format and create a file system on it.  Mount it on /fileshare and unpack backup stuff on it again...

---

