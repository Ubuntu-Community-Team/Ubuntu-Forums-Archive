---
title: "symbolic links across a network"
date: 2006-08-29
forum: Desktop Environments
---

### Post by desimo on 2006-08-29
I was interested creating a symbolic link from one computer to another computer across a network.  What I'd ideally like to do is have only one thunderbird profile folder to control my email client preferences on two different computers (both are running the same version of Ubuntu).

Is this possible with a symbolic link?  Is it advisable?

I've tried something like "ln -s /home/user/existingfile | ssh xx.xx.xx.xx /home/user/newlink" but I am unsure of the syntax...

TIA,
desimo

---

### Post by darkshadow on 2006-08-29
You can't symlink like that but you can mount a directory from your other machine through sshfs then symlink to the file from it's mounted directory.

I have not tested this but these instructions seem good

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by desimo on 2006-08-29
Thanks for the info.  I'll try it out and post with how it goes...

---

### Post by desimo on 2006-08-29
No problems at all.  The step-by-step explanation was thorough and accurate...

After installing fuseutils, I did these things:

added my username to the group "fuse"
made a new directory to use as a mountpoint (must be empty)

changed the permissions of /usr/bin/fusermount
changed the permissions of /dev/fuse

logged in as root

issued a command like this:
```
sshfs xx.xx.xx.xx:path/to/remote/ /local/mount/dir/
```

---

