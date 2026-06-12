---
title: "get files from SSH server onto client machine"
date: 2009-01-16
forum: General Help
---

### Post by porchrat on 2009-01-16
Hi all

Is this possible?  Right now I run an openSSH server and I would like to know if it is possible to have a client machine download something from the server machine?  Does "scp" do this?  I've only ever used "scp" to move files from a client machine to the server, not the other way around.  I've looked at the "man scp" page and it isn't exactly crystal clear on this.

Thanks all

---

### Post by amauk on 2009-01-16
yep, scp is what you're after

[noparse]scp user@remote:/path/to/file.blah /local/path/[/noparse]

---

### Post by Peter09 on 2009-01-16
Add the 'connect to server' applet to you top panel. That will manage it for you. It gives you a file manager view of the remote machine and allows drag and drop activities.

---

### Post by vanadium on 2009-01-16
...and in addition to the above, you can use sshfs from the command line as another way to mount the file system of the remote server locally.

---

### Post by Haiyadragon on 2009-01-16
You could also use sftp. Sftp also works in Nautilus. Just type sftp://user@host:port in the address bar.

---

### Post by porchrat on 2009-01-22
Thank you all for your replies.  I did it with scp, but it is nice to know that there are alternatives, once again this forum didn't let me down.

(sorry I would normally mark this thread "SOLVED", and give you all a proper "Thanks", but for some reason those options are unavailable? - probably connected to the server being down the other day)

---

