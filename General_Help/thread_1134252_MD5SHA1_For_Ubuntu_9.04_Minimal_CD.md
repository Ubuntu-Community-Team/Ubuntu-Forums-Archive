---
title: "MD5/SHA1 For Ubuntu 9.04 Minimal CD?"
date: 2009-04-23
forum: General Help
---

### Post by adamlau on 2009-04-23
Are the MD5/SHA1 hashes for the mini.iso offerings available somewhere? 
I obtained the following hashes for following the _64-bit PC (amd64)_ package: 

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/mini.iso)

MD5: 2b5178d7fc2c758e1973e5d971a6d9bc
SHA1: c568191e31c5a7261b7124788f724c7e153a4e23

Can someone confirm these hash strings?

---

### Post by anonymous_user on 2009-04-24
Well I can confirm the MD5:
```
[kevin]/media/Downloads/Downloads$ md5sum mini.iso
2b5178d7fc2c758e1973e5d971a6d9bc  mini.iso
```

---

### Post by adamlau on 2009-04-24
Thanks, though the hashes ought to be officially published somewhere...

---

### Post by DarkN00b on 2009-04-25
Official Ubuntu MD5SUMS are [here]("https://help.ubuntu.com/community/UbuntuHashes"). Don't see mini there though.

---

### Post by Arch2 on 2009-04-26
After some hunting I found the md5 here...

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/MD5SUMS](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/MD5SUMS)

and for i386...

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/MD5SUMS](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/MD5SUMS)

---

