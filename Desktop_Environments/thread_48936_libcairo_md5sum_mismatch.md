---
title: "libcairo md5sum mismatch"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Bagleemo on 2005-07-14
In trying to upgrade firefox, apparently libcairo is bad.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)
  MD5Sum mismatch

Did this once, cleared my cache (using synaptic in Kubuntu), and it did it again. Any ideas?

-A

---

### Post by IchBin on 2005-07-14
[QUOTE=Bagleemo]In trying to upgrade firefox, apparently libcairo is bad.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)
  MD5Sum mismatch

Did this once, cleared my cache (using synaptic in Kubuntu), and it did it again. Any ideas?

-A[/QUOTE]
 Some people have been having problems like this with the US repo's. Try changing all your repository lines without the "us" part in them. So your repo lines should look like this.
[http://archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)

Then issue a sudo apt-get update. That should fix your problem.

---

