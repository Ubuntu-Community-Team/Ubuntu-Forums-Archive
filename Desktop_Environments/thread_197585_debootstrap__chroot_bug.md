---
title: "debootstrap / chroot bug?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by jpkotta on 2006-06-16
I want a chroot.  I followed [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) to set it up before with Breezy, with essentially no problems.  Now I want to do it again, on a different computer with Dapper.  And I have a weird bug.

I have a spare partition mounted at /archive.  I made a subdir in there to hold the chroot and ran debootstrap.  It seems to run smoothly, until it does a final chroot test, and dies with the error
> W: Failure trying to run: chroot /archive/tech_cd/dapper mount -t proc proc /proc
When I try to chroot, 
> 
root@euler:/ # chroot /archive/tech_cd/dapper/
chroot: cannot run command `/bin/bash': Permission denied
root@euler:/ # chroot /archive/tech_cd/dapper/ /bin/bash 
chroot: cannot run command `/bin/bash': Permission denied
root@euler:/ # chroot /archive/tech_cd/dapper/ /archive/tech_cd/dapper/bin/bash 
chroot: cannot run command `/archive/tech_cd/dapper/bin/bash': No such file or directory
root@euler:/ # 
Then I tried putting it straight under /, so that it's on the same physical partition as /.  Then it worked.  Thinking back, the chroot I made on Breezy with the other computer was the same way, i.e. the chroot dir was on the same partition as /.  

Is this a bug?  Can someone else verify this?

---

### Post by jpkotta on 2006-06-16
Nevermind, I had noexec set for that device when I mounted it.

---

### Post by Sam Liu on 2007-05-10
I know this thread is really old but it came up in google for me so I'll post a little something in case someone needs it

My dapper-> edgy killed my ubuntu, and I needed to get on a terminal to use aptitude to fix it. So what I did was exactly what he did, except that I found it nessecary to use

```
sudo umount /dev/sda3  (/dev/sda3 is my linux partition)
sudo mkdir /mnt/a 
sudo mount /dev/sda3  /mnt/a
sudo chroot /mnt/a
```

and then I did what I needed (aptitude install ubuntu-desktop)

So yeah. just in case someone wanted to know.

(all on a feisty liveCD)

---

