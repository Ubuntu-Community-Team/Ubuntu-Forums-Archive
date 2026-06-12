---
title: "sshfs fstab permissions problem"
date: 2009-06-20
forum: General Help
---

### Post by dranorter on 2009-06-20
Hi, I'm trying to set up an sshfs folder in my home directory which contains my work computer's home directory. Mounting by the sshfs command works fine, but I was hoping to do something more automatic.

I've got this line in my fstab:
```
sshfs#user@host.cmich.edu: /home/user/Notes\040sync fuse noauto,rw,user 0 0
```

However, I've tried lots of other options too, setting the uid to mine, adding defaults, adding nosuid. Nothing seems to have an effect on the permissions of the mounted filesystem. It invariably doesn't even have read permissions for anyone but root. How do I make the mounted file system owned by me instead of root?

...

ok, I guess I'm having better google luck today than last night. The relevant option is allow_other. But this would mean any user can rw, right? Is there a better way of doing this?

(My ultimate goal here, by the way, is synchronizing tomboy notes.)

---

### Post by mali2297 on 2009-06-20
How do you mount the file system? As root?

You should be able to mount the file system as an ordinary user once you added yourself to the 'fuse' group. See [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS).

---

### Post by dranorter on 2009-06-20
Oh, I didn't think about that, thanks!

Now what I want to do is try to mount automatically whenever the folder is used, ie by tomboy. Otherwise it ends up syncing to the local folder if I forget to mount.

In addition if I disconnect from the Internet and then do ls in my home directory, right now it freezes up because it tries to list the folder. How could I get around that?

---

### Post by mali2297 on 2009-06-20
If you want to sync folders between two computers, wouldn't it be better to use something like *rsync*? Perhaps setting it up as a cron job so that it syncs the folders every x minutes.

---

### Post by dranorter on 2009-06-22
Cool, that sounds good.

(I keep having problems with sshfs; right now it shows permissions as rwxrwxrwx and lets me create files but not edit them!) All files mount readonly.)

---

### Post by dranorter on 2009-06-22
Hmm, using rsync the tomboy synchronization seems to work dependent on the order I do things in. If I change something in a note, tell tomboy to sync, then rsync laptop to server, then sync my notes on my server (work computer I should say), the change gets noticed. However if I rsync server to laptop first this naturally deletes the change, but furthermore Tomboy doesn't fix the deletion upon another sync.

Well anyway there must be a way to get rsync to decide which way needs syncing first, I'll keep looking around.

---

