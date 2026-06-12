---
title: "VPN install not working"
date: 2005-12-12
forum: General Help
---

### Post by onejoy on 2005-12-12
I need a vpn client to access my school's wireless network.  When I tried following the school's steps to install it, it said to download the source file, then put in

```
zcat vpnclient-linux-x86_64-4.7.00.0640-kt.tar.gz | tar xvf -
```

by accident i put in

```
zcat vpnclient-linux-x86_64-4.7.00.0640-kt.tar.gz
```

at first and now when i execute the right command, i get

```
zcat: vpnclient-linux-x86_64-4.7.00.0640-kt.tar.gz: unexpected end of file
tar: Read 7249 bytes from -
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

I have no idea what to do.

---

### Post by DrBair on 2005-12-12
Seems like the download was incomplete or corrupted as there is no End Of File.  Try downloading the sources again.

Using the command "tar -zvxf filename.tar.gz" will save you a bit of typing and will accomplish the same task.  Some versions of tar didn't have support for gzip files which I suppose is why they have you use zcat. Take a look at the man page for more details on that.

---

