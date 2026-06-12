---
title: "Problem compiling nautilus-sendto"
date: 2006-02-26
forum: Desktop Environments
---

### Post by Razziel on 2006-02-26
Hi friends.

I'm trying to build the nautilus-sendto package but it's send me this error: ```
dpkg-deb: construyendo el paquete `nautilus-sendto' en `../nautilus-sendto_0.4-0ubuntu4_i386.deb'.
 dpkg-genchanges
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
Now signing changes and any dsc files...
 signfile nautilus-sendto_0.4-0ubuntu4.dsc Daniel Holbach <dh@mailempfang.de>
gpg: skipped "Daniel Holbach <dh@mailempfang.de>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 788:
running debsign failed
root@rexlairs:/home/karnaugh/fuentes-blue#
```

How can I avoid it?

Thanks

---

