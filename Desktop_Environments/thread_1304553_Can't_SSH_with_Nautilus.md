---
title: "Can't SSH with Nautilus"
date: 2009-10-29
forum: Desktop Environments
---

### Post by schurtek on 2009-10-29
I used to be able to SSH into servers from my Nautilus. This allowed me to manipulate files as if they were on my own PC. However, lately I can't get in? It says:

Could not display "sftp://name@host/".

Error: Timed out when logging in
Please select another viewer and try again.


where name is my login name for the ssh and host is the server FQDN.

I can still SSH from Bash, so the problem is not on the server.

---

### Post by schurtek on 2009-10-29
NVM

I went to my home folder, enabled SHOW HIDDEN FILES and deleted the folder .ssh

now it works...

---

### Post by Wildscot on 2009-11-05
Genius! I'd been racking my brains for an answer to this one for days. So simple but it worked for me too.

Cheers

> **schurtek said:**
> NVM

I went to my home folder, enabled SHOW HIDDEN FILES and deleted the folder .ssh

now it works...

---

