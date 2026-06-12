---
title: "does GPG error very serious?"
date: 2005-12-13
forum: General Help
---

### Post by baosheng on 2005-12-13
when I add some apt source into my /etc/apt/source.list ,I faced to some error after running "apt-get update"
does these error will keep me retrieving softwares?
how can i fix it?
I have tried to refer to [http://www.ubuntuforums.org/showthread.php?t=22279](http://www.ubuntuforums.org/showthread.php?t=22279)
but the error still exists.


W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: [http://non-us.debian.org](http://non-us.debian.org) stable/non-US Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: [http://security.debian.org](http://security.debian.org) stable/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

---

### Post by jasay on 2005-12-13
Those are all debian repos.  They are not neccesairly compatible with ubuntu, in fact they could mess over you install pretty badly.  [Here]("http://www.psychocats.net/linux/sources.php") is a list of ubuntu repos.  If you're looking for multimedia codecs not in the official repos, check out the [restricted media wiki page]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29")

---

### Post by redgilda on 2005-12-19
```
W: GPG error: http://ftp.us.debian.org experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: You may want to run apt-get update to correct these problems

```
im getting this error when trying to follow the advice here:

> The official binary packages are mantained by Robin Verdujin
and are available from

    http://ftp.<country>.debian.org/debian/pool/main/k/kvirc/

e.g. for i386:

[http://ftp.us.debian.org/debian/pool/main/k/kvirc/kvirc-data_3.2.0-1_all.deb](http://ftp.us.debian.org/debian/pool/main/k/kvirc/kvirc-data_3.2.0-1_all.deb)

[http://ftp.us.debian.org/debian/pool/main/k/kvirc/kvirc-dev_3.2.0-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/k/kvirc/kvirc-dev_3.2.0-1_i386.deb)
    [http://ftp.us.debian.org/debian/pool/main/k/kvirc/kvirc_3.2.0-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/k/kvirc/kvirc_3.2.0-1_i386.deb)

Debian users can automatically update from KVIrc 2.x by adding the following
line
to their /etc/apt/sources.list:
    deb http://ftp.<country>.debian.org/debian/ experimental main

all I want is to update Kvirc to a 3.2 version in an easy way :D could anyone help me?

---

