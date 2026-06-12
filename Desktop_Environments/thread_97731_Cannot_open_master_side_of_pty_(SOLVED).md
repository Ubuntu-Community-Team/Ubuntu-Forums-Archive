---
title: "Cannot open master side of pty (SOLVED)"
date: 2005-12-01
forum: Desktop Environments
---

### Post by r0ll3r on 2005-12-01
Some people may notice that when starting mc (midnight commander) the following error message shows up:
Cannot open master side of pty: No such file or directory(2)

I am not sure what caused this (kernel upgrade?), but the solution is the following:
edit /etc/fstab, insert this line, somewhere after (below) mounting the root (/):
```
none  /dev/pts  devpts  mode=0620    0    0
```

then mount it:
```
sudo mount -a
```

I had no problems regarding this error message, but anyway, now it's gone, so i wonder why it wasn't included in my fstab file by default. (breezy pre 5.10). Please do not reply to this thread, i don't need any replies. I submitted this thread for helping the ubuntu community. People who need this, might search and find that thread.

---

### Post by eli_d on 2006-01-15
thank you SO MUCH.  i was getting the same error "cannot open master pty", when trying to use Gftp to connect to an SFTP using SSH.  Adding the above line to the /etc/fstab, fixed it.

*bravo!*

---

### Post by oblus on 2006-12-11
hi i have same problem but im using debian (sid) and someday i added repositories of dapper to my sources.list of apt, then i used "apt-get update" and "apt-get -f dist-upgrade"... 
after reboot i has kernel panic on "mdadm" so i tried to bring back old kernel to work by livecd... i changed sources.list to old one without dapper repositories and update,dist-upgrade..
now everything work fine without midnight commander (mc)

i figured out that i dont have /dev/pty
what can i do to fix this?

---

