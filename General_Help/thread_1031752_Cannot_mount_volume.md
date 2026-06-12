---
title: "Cannot mount volume"
date: 2009-01-05
forum: General Help
---

### Post by BartGunn on 2009-01-05
Hi,
I'm trying to connect an external hard drive with all my audio files stored on it and am getting error message 'Cannot mount volume Operation not supported Mount is denied because NTFS is marked to be in use'.
I am an Ubuntu novice and would really appreciate a simple step by step guide to fix this and get my HD installed.
Cheers!
Bart

---

### Post by Crafty Kisses on 2009-01-05
It would appear from that error message Ubuntu is not able to read off of that drive. Try the following command, and see if you get any luck:
```
sudo mount -a
```

---

