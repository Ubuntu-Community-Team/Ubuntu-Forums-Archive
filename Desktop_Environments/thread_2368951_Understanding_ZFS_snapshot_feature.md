---
title: "Understanding ZFS snapshot feature"
date: 2017-08-17
forum: Desktop Environments
---

### Post by danik56 on 2017-08-17
I have installed Ubuntu 17.04 into a ZFS file system.
The ROOT is mounted at /zpool1/os/ubuntu
then I took a snapshot of  zpool1/os/ubuntu and the size of the snapshot was less than 5GB.

Next I created another file system at /zpool1/os/myfiles and copied in around 35GB of data files.

Now, when I take a snapshot of zpool1/os/ubuntu the size of the snapshot is 40GB.  Is this normal ?

---

