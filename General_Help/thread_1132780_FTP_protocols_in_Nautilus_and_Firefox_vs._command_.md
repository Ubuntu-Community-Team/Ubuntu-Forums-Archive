---
title: "FTP protocols in Nautilus and Firefox vs. command line"
date: 2009-04-22
forum: General Help
---

### Post by leandromartinez98 on 2009-04-22
I can connect to a ftp server (with login) through the command line,
but I cannot connect to it either through Nautlius (places -> connect to server) or through firefox ([ftp://server](ftp://server)...), apparently those not
being able to read the content of the remote directory. Since both programs are affected, the problem must be in some under-the-hood ftp program/protocol they use in common, and I would like to test this more specifically to eventually fill a bug report. Anyone knows which is the way Nautilus and Firefox connect to ftp servers? Is it possible to use the same protocol through the command line so to get more detailed error reports?

Thanks.

---

### Post by leandromartinez98 on 2009-04-22
The program used seems to be "gvfs". But what protocol gvfs uses? Anyway, filled this bug report: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/365089](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/365089)

---

