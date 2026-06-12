---
title: "chroot build environments"
date: 2012-08-04
forum: Desktop Environments
---

### Post by Mahler122 on 2012-08-04
Why does the following procedure fail:

```
mkdir -p /home/user/chroot/{bin,lib}
sudo mount --bind /bin /home/user/chroot/bin
sudo mount --bind /lib /home/user/chroot/lib
sudo chroot /home/user/chroot
```

I am getting the following error:

```
chroot: failed to run command `/bin/bash': No such file or directory
```

The thing is /home/user/chroot/bin/bash exists since I bind mounted the directory.

In addition, there are procedures which bind mount proc and sys and then chroot into a livecd or something at which point proc and sys are available.

So basically, why doesn't the chroot know about the bind mounted /bin/bash? Why is this procedure I'm doing incorrect? I figure for what I'm doing I don't need proc or sys and that I would get other errors if not including them int he chroot was causing the problem.

---

