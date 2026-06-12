---
title: "apt-get is dead"
date: 2009-05-14
forum: Desktop Environments
---

### Post by vasluianuliviu on 2009-05-14
Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status/



after an force shut down cause the damn thing frozen, when i try to "apt-get update "and the message is the one from abovehow can i fix this

---

### Post by sahabcse on 2009-05-14
Hi

Try the following

sudo rm -f /var/lib/dpkg/lock
cd /var/lib/dpkg
mv status status-bad
cp status-old status

apt-get update

---

### Post by vasluianuliviu on 2009-05-14
after that he can download anything from any server

: Can't dowload [http://ftp.lug.ro/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.27-2ubuntu2_i386.deb](http://ftp.lug.ro/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.27-2ubuntu2_i386.deb)
  404 Not Found [IP: 83.166.201.99 80] to any packages


repaired changed the download server and is updating.


then a new one

Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle

---

