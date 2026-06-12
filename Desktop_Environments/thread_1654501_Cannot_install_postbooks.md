---
title: "Cannot install postbooks"
date: 2010-12-28
forum: Desktop Environments
---

### Post by mnky3820 on 2010-12-28
Uname -a: Linux rjtewalt-P-7801u 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

I am fairly new to ubuntu and linux.  I am trying to install postbooks by xTuple on ubuntu 10.10.  The installer runs to the end and during its "initdb" step I get the following error in a dialog popup:

> There has been an error.
/opt/xTuple/postgresql/bin/initdb: error while loading shared libraries: libaudit.so.0: cannot open shared object file: No such file or directory
The application will exit now.

I have installed the libaudit0 package and can find it in two places:

> rjtewalt@rjtewalt-P-7801u:/lib$ ls -ll libaudit*
lrwxrwxrwx 1 root root     17 2010-12-28 01:51 libaudit.so.0 -> libaudit.so.0.0.0
-rw-r--r-- 1 root root 104936 2010-06-30 23:34 libaudit.so.0.0.0


rjtewalt@rjtewalt-P-7801u:/lib64$ ls -ll libaudit*
lrwxrwxrwx 1 root root     17 2010-12-28 01:51 libaudit.so.0 -> libaudit.so.0.0.0
-rw-r--r-- 1 root root 104936 2010-06-30 23:34 libaudit.so.0.0.0

But when I check for the shared libraries on the initdb executable, it cannot find the libaudit.so.0:

> rjtewalt@rjtewalt-P-7801u:/opt/xTuple/postgresql/bin$ ldd initdb 
	linux-gate.so.1 =>  (0xf779b000)
	libxslt.so.1 => /opt/xTuple/postgresql/bin/./../lib/libxslt.so.1 (0xf7769000)
	libxml2.so.2 => /opt/xTuple/postgresql/bin/./../lib/libxml2.so.2 (0xf7661000)
	libpam.so.0 => /opt/xTuple/postgresql/bin/./../lib/libpam.so.0 (0xf7655000)
	libssl.so.4 => /opt/xTuple/postgresql/bin/./../lib/libssl.so.4 (0x07638000)
	libcrypto.so.4 => /opt/xTuple/postgresql/bin/./../lib/libcrypto.so.4 (0x0766e000)
	libkrb5.so.3 => /usr/lib32/libkrb5.so.3 (0xf758a000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7574000)
	libreadline.so.4 => /opt/xTuple/postgresql/bin/./../lib/libreadline.so.4 (0x05932000)
	libtermcap.so.2 => /opt/xTuple/postgresql/bin/./../lib/libtermcap.so.2 (0x00af4000)
	libcrypt.so.1 => /lib32/libcrypt.so.1 (0xf7542000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf753e000)
	libm.so.6 => /lib32/libm.so.6 (0xf7517000)
	libc.so.6 => /lib32/libc.so.6 (0xf73bc000)
	libaudit.so.0 => not found
	libgssapi_krb5.so.2 => /usr/lib32/libgssapi_krb5.so.2 (0xf738d000)
	libcom_err.so.2 => /lib32/libcom_err.so.2 (0xf7389000)
	libk5crypto.so.3 => /usr/lib32/libk5crypto.so.3 (0xf7364000)
	libresolv.so.2 => /lib32/libresolv.so.2 (0xf7350000)
	libkrb5support.so.0 => /usr/lib32/libkrb5support.so.0 (0xf7348000)
	libkeyutils.so.1 => /lib32/libkeyutils.so.1 (0xf7344000)
	/lib/ld-linux.so.2 (0xf779c000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf732b000)

I have tried running ldconfig, but it hasn't helped.  Any suggestions would be greatly appreciated, thank you.

---

### Post by thefix25 on 2010-12-30
The libaudit package on a 64 bit system doesn't install 32 bit libs.  You have to copy libaudit.so.0.0.0 off of a 32 bit system into lib32 and create a symlink to it named libaudit.so.0 and you should be good.

---

### Post by jojoroto on 2011-01-08
> **thefix25 said:**
> The libaudit package on a 64 bit system doesn't install 32 bit libs.  You have to copy libaudit.so.0.0.0 off of a 32 bit system into lib32 and create a symlink to it named libaudit.so.0 and you should be good.

Thanks. i had the same problem and i solved it with your intructions.

---

### Post by Piney on 2011-03-26
Hi I'm a linux noob and have no idea how to follow these instructions.
Can anyone please attach this needed file and step by step instructions to fix this issue.

thanks in advance

Piney

---

