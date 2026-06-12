---
title: "[karmic] can't login after apt-get upgrade"
date: 2010-02-06
forum: Desktop Environments
---

### Post by ajcoon on 2010-02-06
Hi all,

I did an apt-get upgrade on my Karmic workstation yesterday and now I can't login to Gnome.  Failsafe Gnome works fine.

I posted quite a bit of detail on this thread on superuser.com:

[http://superuser.com/questions/105354/ubuntu-login-screen-reloads](http://superuser.com/questions/105354/ubuntu-login-screen-reloads)


Would appreciate any assistance with this, thanks.

-aj

---

### Post by mac9416 on 2010-02-06
Hello,

> ...what seems to happen is that after I enter my username and password, the screen temporarily switches to all black, and then the login page is loaded again.

I am, admittedly, shooting in the dark, but I ran into the same problem a few days ago. The problem was that I had run completely out of disk space. After partitioning some more space to Ubuntu from XP, I was able to login like normal.

A day or two after that happened, I ran into this blog post about running Ubuntu on 0 bytes. It might have some helpful info fo you. [http://profarius.com/content/running-0bytes](http://profarius.com/content/running-0bytes)

I hope your problem is as simple as that. Good luck!

---

### Post by ajcoon on 2010-02-06
> **mac9416 said:**
> Hello,



I am, admittedly, shooting in the dark, but I ran into the same problem a few days ago. The problem was that I had run completely out of disk space. After partitioning some more space to Ubuntu from XP, I was able to login like normal.

A day or two after that happened, I ran into this blog post about running Ubuntu on 0 bytes. It might have some helpful info fo you. [http://profarius.com/content/running-0bytes](http://profarius.com/content/running-0bytes)

I hope your problem is as simple as that. Good luck!

Thanks for the suggestion.  I do in fact have plenty of disk space though.  Here is my df:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              28G  4.0G   23G  15% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
udev                  1.5G  260K  1.5G   1% /dev
none                     0     0     0   -  /dev/pts
none                  1.5G  288K  1.5G   1% /dev/shm
none                  1.5G   96K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
none                   28G  4.0G   23G  15% /var/lib/ureadahead/debugfs
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
```


Thanks,
-aj

---

### Post by juan legarda on 2010-02-06
I ran into the same problem, brand new system76 starlight, it is dead now!

---

### Post by mac9416 on 2010-02-06
Ah well, it was worth a shot.
Hopefully someone more knowledgeable will help you out. Good luck!

---

### Post by cgoo on 2010-02-07
How was this solved? I have the same problem.

---

### Post by ajcoon on 2010-02-09
@cgoo - it ended up being my own dumb fault.  I had a bash script in /etc/profile.d that stopped working after the upgrade.  A simple syntax change fixed it.

If you don't have any custom scripts in /etc/profile.d, chances are my solution won't work for you...

---

