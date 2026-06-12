---
title: "rsync help"
date: 2009-02-06
forum: General Help
---

### Post by crokett on 2009-02-06
I've been reading man pages and testing things until my eyes are blurry.  I have rsync working from a windows client to linux server but not exactly the way I want it to work.  The rsync client goes to localhost because I am tunneling through ssh.

Here is the command I am running:
```

rsync -avuz /cygdrive/c/Work me@127.0.0.1::Work --password-file=password

```

Here is rsyncd.conf:
```

uid = me		
gid = me
use chroot = true

[Work]
comment = Work files
path = /home/greendm/
hosts allow = ahost anotherhost
list = yes
read only = no
secrets file = /etc/rsyncd/secrets

```

What happens is with uid and gid set to me then I get access denied trying to create directories.  If I set them to 0 then rsync runs but resets the owner to root so I lose access to the files on the server from my userid and I have to sudo chown to set ownership back.  The paths also aren't quite right either.  'Work' is a directory inside my home directory and I want the files and dirs inside of it synchronized.  What happens is another directory called 'Work' gets created inside of it on the server and the entire directory from the client gets put there.

---

### Post by crokett on 2009-02-06
The answer was to run rsync daemon on the XP machine and use the Linux client to push/pull.  That cleared up a few issues including rsync resetting the permissions on the transferred dirctory to read only by only root. If I use the Windows client  the files wouldn't transfer without -archive option set and with it the permissions get screwed up.

---

