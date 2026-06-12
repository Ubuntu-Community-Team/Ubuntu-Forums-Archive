---
title: "rsync question"
date: 2009-03-19
forum: General Help
---

### Post by mattruffle on 2009-03-19
I'm looking to setup a dedicated server for doing rsync backups. Unfortunatly this can't be done on the machine that controls my storage array, where I'd like to put everything, mostly because I don't want the extra load of rsync running on it. I want it in one place, so it's easy to admin. I will probably be using SSH to help automate the process.

So basically if servers 1-3 are being backed up, I want 4 to do it, and put the files on 5.

I haven't found anything indicating that I can do that. I was thinking about using NFS to mount directories from servers 1-3 that I want to back up onto the rsync (4) server, but I don't know if that's a good idea.

Any ideas would be greatly appreciated. I hope this doesn't come off as a totally dumb question.

All of my boxes are currently using ubuntu 8.10 server. All of the transfers are going to be done inside of my network, behind my firewall.

Thanks!

---

