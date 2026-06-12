---
title: "In Ubuntu 9.04, how do I mount different folders of the same partitions to different"
date: 2010-05-19
forum: Desktop Environments
---

### Post by PhotonicGuy on 2010-05-19
I have a shared NTFS partition ("shared") that I use for data for both  Windows and Ubuntu. How can I mount the music folder on shared to  $Home/Music, and the Videos folder on shared to $Home/Videos? I want to  mount the different folders on the partition to different folders in  home. Any help here? Thanks in advance!

---

### Post by portentum on 2010-05-19
I think what you're actually looking for is linking. (**man ln** for more info)

As an example, I would use
```

ln -s /media/Storage3/Music ~/Music
```
to create a symlink at ~/Music that contains everything that's actually stored at /media/Storage3/Music.

---

