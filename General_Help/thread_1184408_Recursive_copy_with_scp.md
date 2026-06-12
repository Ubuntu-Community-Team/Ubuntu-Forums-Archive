---
title: "Recursive copy with scp"
date: 2009-06-11
forum: General Help
---

### Post by bartoni on 2009-06-11
Must be doing something really stupid here. All I want to do is copy a selection of specific files in various folders from my webserver to my home machine.

I'm using : scp -r *something.jpg [email]me@home.server[/email]:/backup/

This mostly works. It's recursively copying from directories on the webserver to my home machine... except! I'm losing the directory names, everything arrives in the backup folder on my home machine. How do I maintain the directory structure?

Not sure if TARing and then copying that is doable as I have almost 0 free space on my webserver

---

### Post by sahabcse on 2009-06-11
Give the parent folder name for copying, so it copy the all the directory inside the parent directory.

scp -r [email]root@remoteserveripaddress.com[/email]:/home/test/ /backup

---

### Post by nikhilk on 2009-06-11
You can give rsync a try. It supports replicating the entire directory structure and also elaborate filtering mechanisms via the '--filter' option.
It is more suitable for mirroring though (uses lot less bandwidth as it only transfers changes and not the entire file), if you just want to do a one time copy scp -r should be fine.

---

### Post by bartoni on 2009-06-11
> **sahabcse said:**
> Give the parent folder name for copying, so it copy the all the directory inside the parent directory.

scp -r [email]root@remoteserveripaddress.com[/email]:/home/test/ /backup

This doesn't seem to work for me. I want to copy specific files, not just entire directories.

Maybe find with xargs is the answer?

---

### Post by kevashcraft on 2013-04-30
A few years late, but thanks for the info! Works great! :)

scp -r user@host:/folder/ ~/

---

### Post by oldos2er on 2013-04-30
Closed, please don't bump old threads.

---

