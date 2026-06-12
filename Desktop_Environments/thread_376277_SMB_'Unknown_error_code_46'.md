---
title: "SMB 'Unknown error code: 46'"
date: 2007-03-04
forum: Desktop Environments
---

### Post by h6w on 2007-03-04
Hey,

On 64-bit Ubuntu connecting to SAMBA server, I get:
Could not open location 'smb://fileserver/public'
Unknown error code: 46

I have checked with:
tudor@systems:~$ smbclient //fileserver/public
Password: 
Domain=[FILESERVER] OS=[Unix] Server=[Samba 3.0.24]
smb: \> exit

Nothing in the logs.  I suspect it's a regex parsing issue in the Gnome-SMB component.

Any ideas?

Cheers,
Tudor.

---

