---
title: "MP620 pstocanonij missing ldd libraries"
date: 2009-07-04
forum: Desktop Environments
---

### Post by javahollic on 2009-07-04
Hi all,
so setting up an MP620 printer again, had it working in 8.10, 9.04 x86_64 is being difficult.

My problem lies currently the /usr/lib/cups/filter/pstocanonij , its ldd output is:
```

	linux-gate.so.1 =>  (0xf7f1c000)
	libpopt.so.0 => not found
	libcups.so.2 => not found
	libc.so.6 => /lib32/libc.so.6 (0xf7da6000)
	/lib/ld-linux.so.2 (0xf7f1d000)

```

Looking at the same libs on a 8.04 (working) 64bit system gives me:
```

	linux-gate.so.1 =>  (0xffffe000)
	libpopt.so.0 => /lib32/libpopt.so.0 (0xf7f14000)
	libcups.so.2 => /usr/lib32/libcups.so.2 (0xf7ee1000)
	libc.so.6 => /lib32/libc.so.6 (0xf7d91000)
	libgssapi_krb5.so.2 => /usr/lib32/libgssapi_krb5.so.2 (0xf7d68000)
	libkrb5.so.3 => /usr/lib32/libkrb5.so.3 (0xf7cdb000)
	libk5crypto.so.3 => /usr/lib32/libk5crypto.so.3 (0xf7cb8000)
	libcom_err.so.2 => /lib32/libcom_err.so.2 (0xf7cb5000)
	libgnutls.so.13 => /usr/lib32/libgnutls.so.13 (0xf7c40000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7c27000)
	libm.so.6 => /lib32/libm.so.6 (0xf7c02000)
	libcrypt.so.1 => /lib32/libcrypt.so.1 (0xf7bd0000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7bbb000)
	/lib/ld-linux.so.2 (0xf7f35000)
	libkrb5support.so.0 => /usr/lib32/libkrb5support.so.0 (0xf7bb3000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7bae000)
	libkeyutils.so.1 => /lib32/libkeyutils.so.1 (0xf7bab000)
	libresolv.so.2 => /lib32/libresolv.so.2 (0xf7b98000)
	libtasn1.so.3 => /usr/lib32/libtasn1.so.3 (0xf7b88000)
	libgcrypt.so.11 => /lib32/libgcrypt.so.11 (0xf7b3b000)
	libgpg-error.so.0 => /lib32/libgpg-error.so.0 (0xf7b37000)

```

I'm guessing the problem lies with:
```

	libpopt.so.0 => not found
	libcups.so.2 => not found

```

So, yes, they are installed, eg:
```

ldconfig -p | grep libpopt
libpopt.so.0 (libc6,x86-64) => /lib32/libpopt.so.0
libpopt.so.0 (libc6,x86-64) => /lib/libpopt.so.0
libpopt.so.0 (libc6,x86-64) => /usr/lib/libpopt.so.0
libpopt.so (libc6,x86-64) => /usr/lib/libpopt.so

```
and
```

ldconfig -p | grep libcups
libcupsimage.so.2 (libc6,x86-64) => /usr/lib/libcupsimage.so.2
libcups.so.2 (libc6,x86-64) => /usr/lib/libcups.so.2
libcups.so (libc6,x86-64) => /usr/lib/libcups.so

```

So the libraries do exist, but aren't 'found'.  I had a quick go at adding /lib32 for popt.so.0 to /etc/ld.so.conf, but no avail.

Ideas anyone?

Andy

---

### Post by heseekes on 2009-09-17
Hello Andy,

I had the same problem. Thanks for posting your 8.04 ldd output; it helped me to track down a solution.

Link:

                                                                 [http://www.holgermetzger.de/mp620.html](http://www.holgermetzger.de/mp620.html)


The instructions are in German, I think, but easy enough to follow. Here is the library I was missing.

                                                                            ```
sudo apt-get install ia32-libs
```Thanks to you, and to Holger Metzger my mp620 is up and running again!



For any newbs like myself struggling to install this printer on a 64bit version of Ubuntu 9.04, or another distribution based upon it, here are the steps that worked for me:


Downloaded these driver packages:

 *IJ Printer Driver Ver. 2.80 for Linux(debian Common package) 
*IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP610 series)

Link: 

 [http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP610%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP610%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)


Downloaded and extracted these PPD and conf files:

*ppdMP620-630en-1.5.tar.gz

Link: 

[http://sourceforge.net/projects/mp610linux/files/](http://sourceforge.net/projects/mp610linux/files/)



Installed driver:

```
sudo dpkg -i --force-architecture --force-all cnijfilter-common_2.80-1_i386.deb

sudo dpkg -i --force-architecture --force-all cnijfilter-mp610series_2.80-1_i386.deb
```Watched for missing dependencies when installing. Installed what was needed with, sudo apt-get install...


Copied pdd and conf files into place:

```
sudo cp canonmp620-630en.ppd /usr/share/ppd/

sudo cp cifmp610.conf /usr/lib/bjlib/
```Installed the ia32 shared libraries:

```
 sudo apt-get install ia32-libs
```Restarted cups:

```
sudo /etc/init.d/cups restart
```Installed my printer.


Hope this helps...

---

