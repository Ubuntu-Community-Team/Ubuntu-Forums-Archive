---
title: "Nautilus and SSH on non-standard port"
date: 2007-10-15
forum: Desktop Environments
---

### Post by luisfpg on 2007-10-15
Hi all!
I'm using Gutsy RC and I'm having an issue with Nautilus connecting to SSH hosts on a non-standard port (22).
Nautilus gave me a "Nautilus cannot display "ssh://user@host:port/".
When I connect to a host on the standard port, it connects ok.
I can connect normally to the same host with the command line.
Is that a bug with Nautilus or something I'm doing wrong?
Thanks in advance.

**Update:**
When I run *gnomevfs-info ssh://user@server1:22/* it works, but *gnomevfs-info ssh://user@server:2222/* Yields **Error: I/O error**

---

