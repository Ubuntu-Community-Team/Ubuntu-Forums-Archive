---
title: "Cannot mount network drive with unicode support"
date: 2006-08-17
forum: Desktop Environments
---

### Post by natuk on 2006-08-17
I am trying for some time now to mount a network hard drive using:

mount -t smbfs -o lfs,iocharset=utf8,unicode,codepage=unicode //network/location /target/path

Although the drive is mounted, any unicode filenames appear as jiberish (or with ????) and I have tried all sorts of combinations of the above options. The strange thing is that if I browse the network drive from "Network Servers" the filenames appear correctly. Same happens with smbclient as well.

So clearly it is possible to see unicode filenames. Am I missing an option in the mount command?

Thanks

natuk

---

