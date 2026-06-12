---
title: "scp gui - NOT SFTP"
date: 2008-12-25
forum: Desktop Environments
---

### Post by jsprenkl on 2008-12-25
Hello,
Is there an SCP gui front end? I do NOT want an SFTP gui, which is what nautilus/filezilla etc. provide. The server I'm connecting to only supports scp and I'd rather not load more junk on it if what I already have will work.

---

### Post by albinootje on 2008-12-25
> **jsprenkl said:**
> Hello,
Is there an SCP gui front end? I do NOT want an SFTP gui, which is what nautilus/filezilla etc. provide. The server I'm connecting to only supports scp and I'd rather not load more junk on it if what I already have will work.

I have a server which has scponly shells, and it worked fine using the ssh-support inside Gftp.

---

### Post by jsprenkl on 2008-12-25
Thanks :)

Merry Christmas

---

### Post by johny.mnemonic on 2009-04-09
I just tried gftp and it is using sftp, not scp. Secpanel is also not able to connect.
I have dropbear as SSH server on target machine, so I need scp connection, it is the only way to get there.
Any idea?
Only gui client that is working with it is WinSCP on windoze, but on linux I am stuck to command line...

---

### Post by MrZehl on 2009-10-09
WinSCP is working under Wine.

---

