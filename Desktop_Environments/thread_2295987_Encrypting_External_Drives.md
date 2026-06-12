---
title: "Encrypting External Drives?"
date: 2015-09-22
forum: Desktop Environments
---

### Post by nick112 on 2015-09-22
Does anyone know of a good way to encrypt an external drive so that is compatible with both Linux and Windows systems? The linux tool works great for encrypting a drive for use with Linux systems, but I really one that is compatible with Windows as well.

---

### Post by biji on 2015-09-23
If encryption only for linux I use ecyrptfs, using this script to mount:

for a in `ls -d /media/username/*/Private`; do

	echo "mounting: " $a
	sudo mount.ecryptfs $a $a

done

---

### Post by nick112 on 2015-09-23
I can encrypt my external hard drive and it works fine with with Linux. When I plug it into a Windows system, it tells me the drive has not been formatted. I'm looking for an solution that will work with both Linux and Windows.

---

### Post by nick112 on 2015-09-23
I can encrypt my external hard drive and it works fine with with Linux. When I plug it into a Windows system, it tells me the drive has not been formatted. I'm looking for an solution that will work with both Linux and Windows.

---

