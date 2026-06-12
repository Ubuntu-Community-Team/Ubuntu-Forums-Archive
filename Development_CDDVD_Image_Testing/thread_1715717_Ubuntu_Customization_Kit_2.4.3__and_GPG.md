---
title: "Ubuntu Customization Kit 2.4.3  and GPG"
date: 2011-03-27
forum: Development CD/DVD Image Testing
---

### Post by darkfly on 2011-03-27
In the Console I'm trying to add a repository public key to the keyring. But when this happens:

root@gisPU:/# gpg
gpg: fatal: can't create directory `/home/gis/.gnupg': No such file or directory
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768

this is typed at UCK console, why is it looking for the /home/gis ?
Any way to go around this?

---

