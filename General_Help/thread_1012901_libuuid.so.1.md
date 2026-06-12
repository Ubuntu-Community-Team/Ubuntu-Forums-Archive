---
title: "libuuid.so.1"
date: 2008-12-16
forum: General Help
---

### Post by any.linux12 on 2008-12-16
hi!

I'm trying to install a business software in a ubuntu server 8.04 64bit.
And when I'm installing it sends me an error saying something like:
> 
AbaSetup: error
---------------

Exception: The helper process returned an unexpected result (127,
/opt/abacus/psql/bin/psregsvr /opt/abacus/psql/lib/libbdumsgrb.so.10)

/opt/abacus/psql/bin/psregsvr: error while loading shared libraries:
libuuid.so.1: cannot open shared object file: No such file or directory


How can I make it load the libuuid.so.1

---

### Post by PmDematagoda on 2008-12-16
Try running:-
```
sudo ldconfig
```
and then run the installer again.

---

### Post by any.linux12 on 2008-12-16
when I type that just appears this:

/sbin/ldconfig.real: File /usr/lib/libstdc++.so.6.0.2 is empty, not checked.

is it important??

---

### Post by PmDematagoda on 2008-12-16
> **any.linux12 said:**
> when I type that just appears this:

/sbin/ldconfig.real: File /usr/lib/libstdc++.so.6.0.2 is empty, not checked.

is it important??

No, it's not important. Did you try installing the software now?

---

### Post by any.linux12 on 2008-12-17
/opt/abacus/psql/bin/psregsvr: error while loading shared libraries:
libuuid.so.1:  wrong ELF class: ELFCLASS64

now I know that the problem is that I'm using ubuntu server 64 bit and the libraries aren't compatible

then when I check the ldd of the file with error
> 
esp-admin@espVSRV01:/opt/abacus/psql/bin$ ldd psregsvr 
	linux-gate.so.1 =>  (0xffffe000)
	libpscore.so.3 => not found
	libpscl.so.3 => not found
	libuuid.so.1 => not found
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ef3000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7eef000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7dfc000)
	libm.so.6 => /lib32/libm.so.6 (0xf7dd7000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7dcb000)
	libc.so.6 => /lib32/libc.so.6 (0xf7c7c000)
	/lib/ld-linux.so.2 (0xf7f17000)


How do I connect the right libraries to run this thing????

Please help

---

### Post by any.linux12 on 2008-12-17
more info:
> 
root@espVSRV01:/opt/abacus/psql/bin$ sudo ld psregsvr 
ld: i386 architecture of input file `psregsvr' is incompatible with i386:x86-64 output
ld: error in psregsvr(.eh_frame); no .eh_frame_hdr table will be created.
ld: warning: cannot find entry symbol _start; defaulting to 0000000000403250


---

### Post by PmDematagoda on 2008-12-17
How old is this software? Is it from the repositories?

---

