---
title: "SSH Error: &quot;/sbin/nologin: No such file or directory&quot;"
date: 2023-01-02
forum: Desktop Environments
---

### Post by dbee on 2023-01-02
I can't login to my remote server guys. I get this error...

```
/sbin/nologin: No such file or directory
```

from SSH on the bash shell. I can't find an answer to this on Google.

I've done a...

```
sh-add ~/.ssh/id_rsa
```

no luck

```

localhost: ssh_hostinger
/sbin/nologin: No such file or directory
Connection to 145.14.153.XXX closed.
localhost: stat /sbin/nologin
  File: /sbin/nologin
  Size: 14640     	Blocks: 32         IO Block: 4096   regular file
Device: 10305h/66309d	Inode: 8918066     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-02 10:19:21.676016416 +0000
Modify: 2022-11-24 12:05:18.000000000 +0000
Change: 2022-11-28 18:00:53.860011250 +0000
 Birth: 2022-11-28 18:00:53.808011229 +0000


```

---

### Post by dbee on 2023-01-02
Someone deactivated SSH on my web host.

I logged into the web panel on my web host and re-enabled SSH.

Worked fine then.

---

