---
title: "Grsync to server via SSH help"
date: 2009-03-03
forum: General Help
---

### Post by scoobyNZ on 2009-03-03
Hello,

I am trying to back-up from my Desktop (Ubuntu 8.10) on 192.168.2.2  to my server on 192.168.2.20.

I am using Grsync at the moment but am unable to get past errors.

The command that Grsync is trying is (this is the simulation)

rsync -r -n -t -o -v --progress -l -e ssh /home/craig/Documents/backup/ 192.168.2.20:/home/craig/backup/

I get the oppurtunity to input the password for the user craig on the server (192.168.2.20) but get the following error, 

[I]bash: rsync: command not found

rsync: connection unexpectedly closed (0 bytes received so far) [sender]

rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3][/I]

I can connect to the server via SSH so I do not think it is the SSH connection – can anyone who knows about rsync see any problems with the commands?

Many thanks,
C

---

### Post by scoobyNZ on 2009-03-03
Solved - needed to install rsync on server machine as well as desktop.

---

### Post by mdrmike on 2010-11-15
I ran into this problem, but didn't have the option to install rsync on the server.  Used sshfs to get around the problem of not having rsync on the server by fooling rsync to think it was a simple local sync.

I needed to do this for a client that was using godaddy - and rsync is either not installed or has restricted access.


to install sshfs and setup a mount do this from a shell
```

##install sshfs
#sudo apt-get install sshfs

##create a folder to mount
#mkdir ~/remote-host-mount

##mount the remote host
#sshfs user@host:/path-to-mount-on-server/ ~/remote-host-mount -o idmap=user -o follow_symlinks

```

Every program on your desktop now has access to those files, just as if they were local.  Its not as fast as NFS or the like, but sure is handy,,, and not noticeably slow.


to unmount, do this from shell
```
##unmount remote host
#fusermount -u ~/remote-host-mount
```

---

