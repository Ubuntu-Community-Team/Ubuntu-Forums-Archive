---
title: "amarok 1.4.3"
date: 2006-09-13
forum: Desktop Environments
---

### Post by termite on 2006-09-13
I'm trying to upgrade amarok to 1.4.3, but I'm getting an MD5 checksum mismatch when trying to update dapper backports:
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2)  MD5Sum mismatch

I've added Jonathan Riddell's key as specified at [http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php)

any ideas?

---

### Post by neoeden on 2006-09-14
md5sum is calculated from the file downloaded, so the key shouldn't matter. Try apt-get update ing and try again. It could also be an issue w\ the mirror, googling around has shown that stuff like this happens before.

---

### Post by orb9220 on 2006-09-14
Jonathan Riddell's key has always produced errors for me. I disregard and continue with the install.

---

