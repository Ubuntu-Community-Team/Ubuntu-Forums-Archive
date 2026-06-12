---
title: "NFS Client on 18.04: Not TAB completion while mounting"
date: 2020-03-26
forum: Desktop Environments
---

### Post by Alex_K. on 2020-03-26
Hello everyone,

Lately I moved from 14.04 on my PC, to 18.04 (clean install). Unfortunately, one thing behaves differently and I wasn't been able to solve it - while mounting NFS (from another Linux at home), upon writing "sudo mount -t nfs -o v3 x.x.x.x:" and hitting TAB, the remote /folder, does not complete on its own. If I write the exact (remote) path down, all is working. But what went wrong and how do I solve it? Auto completion work perfectly on 14.04 (no settings were needed and remote NFS server is obviously the same for both versions), how do I restore it on 18.04?

Thank you.

---

### Post by TheFu on 2020-03-27
I'd never thought to try that.  Would only expect it to work if ssh was working, using ssh-keys for authentication from the NFS client to the NFS server.

BTW, moving off 14.04 only a year too late. Nice.

---

