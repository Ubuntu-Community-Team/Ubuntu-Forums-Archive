---
title: "I think I screwed up my SSH client, do I have to reinstall?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Stochastic on 2006-09-05
Hey, I was trying to reconfigure my ssh because I reinstalled my server(thus a new RSA key) and in the process I accidentally removed the contents of the /home/me/.ssh/known_hosts file and now I can't seem to use ssh.  Any help would be appreciated.  Thanks.

---

### Post by taurus on 2006-09-05
Just create an empty file and you are all set again...

```
touch ~/.ssh/known_hosts
```

---

