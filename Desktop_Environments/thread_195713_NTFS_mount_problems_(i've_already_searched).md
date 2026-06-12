---
title: "NTFS mount problems (i've already searched)"
date: 2006-06-13
forum: Desktop Environments
---

### Post by xen on 2006-06-13
Hey there folks! I'm having a few problems with reading my NTFS partitions.

Here's the story: All my NTFS partitions were readable yesterday, nothing has changed as far as i'm aware other than that I compiled a new kernel using the ck12 patchset.

I've checked various NTFS mouting guides and my /etc/fstab is fine! 

The strange thing is the NTFS (windows) partition on HDD #1 works fine, I just can't get the partitions on HDD #2 to work.

Upon running 'sudo mount -a' I get the followng error message:

```
mount: /dev/hdb5 already mounted or /media/hdb5 busy
mount: /dev/hdb6 already mounted or /media/hdb6 busy

```

And if I try changing the mount directory of one of them:

```
mount: /dev/hdb5 already mounted or /windows busy
mount: /dev/hdb6 already mounted or /media/hdb6 busy

```

So really i'm pretty stumped! If I try unmounting those 2 partitions using umount, it says they are not mounted, so it makes me think there is something wrong with the mount directories?

Any help is appreciated!

---

### Post by xen on 2006-06-13
FIXED!

See: [http://ubuntuforums.org/showthread.php?t=175693](http://ubuntuforums.org/showthread.php?t=175693)

---

