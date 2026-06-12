---
title: "apt-get install elfutils"
date: 2009-03-18
forum: General Help
---

### Post by big136 on 2009-03-18
Hi,
issuing the following :
eu-readelf -n /lib/tls/libc-2.3.3.so
Ireceive :
The program 'eu-readelf' is currently not installed.  You can install it by typing:
apt-get install elfutils
Make sure you have the 'universe' component enabled
bash: eu-readelf: command not found

Then I try to install :
apt-get install elfutils
But I receive :
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/universe libelf1 0.123-2
  404 Not Found
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/universe elfutils 0.123-2
  404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/universe/e/elfutils/libelf1_0.123-2_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/e/elfutils/libelf1_0.123-2_i386.deb)  404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/universe/e/elfutils/elfutils_0.123-2_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/e/elfutils/elfutils_0.123-2_i386.deb)  404 Not Found

Can you help me ?
Thank you.

---

### Post by pmlxuser on 2009-03-18
if you click the link you will realize that the file doesnot exit on the fr.archive.

you can get it from the following and do a manual install

[http://ubuntu.nad.go.id/ubuntu/pool/main/e/elfutils/](http://ubuntu.nad.go.id/ubuntu/pool/main/e/elfutils/)

---

### Post by big136 on 2009-03-18
> **pmlxuser said:**
> if you click the link you will realize that the file doesnot exit on the fr.archive.

you can get it from the following and do a manual install

[http://ubuntu.nad.go.id/ubuntu/pool/main/e/elfutils/](http://ubuntu.nad.go.id/ubuntu/pool/main/e/elfutils/)

Thank you,
Which on of following should I download :
[ ]	libasm-dev_0.131-4_i386.deb	05-May-2008 14:03 	22K
[ ]	libasm1_0.131-4_i386.deb	05-May-2008 14:03 	21K
[ ]	libdw-dev_0.131-4_i386.deb	05-May-2008 14:03 	92K
[ ]	libebl-dev_0.131-4_i386.deb	05-May-2008 14:03 	61K
[ ]	libelf-dev_0.131-4_i386.deb	05-May-2008 14:03 	58K
[ ]	libelf1_0.131-4_i386.deb	05-May-2008 14:03 	45K

Thank yoy.

---

### Post by pmlxuser on 2009-03-18
usually -dev are in development stage so best download would be

[ ] libelf1_0.131-4_i386.deb 05-May-2008 14:03 45K
[ ] libasm1_0.131-4_i386.deb 05-May-2008 14:03 21K

if you try to install you might be told that it depends on another package possibly from the same list. if me was you i would download the 2 try to install if more is needed it would be in the -dev.debs

---

