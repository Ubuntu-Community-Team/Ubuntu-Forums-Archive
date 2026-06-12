---
title: "YSFlight gives off error referring to libgomp, cannot get it to work"
date: 2014-05-10
forum: Gaming &amp; Leisure
---

### Post by arazgriz25 on 2014-05-10
I'm trying to get a server running YSFlight, a Flight Simulator for Windows, Mac and Linux. when i run the Linux version, it gives a error in the console that says:

```
./ysflight-consvr: error while loading shared libraries: libgomp.so.1: cannot open shared object file: No such file or directory

```
I went to ysfhq.com, which is a community for the site, one of them told me to try installing the Libgomp packages, i did that, nothing.
I'm running Ubuntu 13.04 with 1GB Ram, and a 2.50GHz Intel Xeon Processor.

---

### Post by MikeCyber on 2014-05-11
try:
ldd ysflig*
it should show missing libs that you need to install. Probably you've installed a older lib or it's missing a symlink to *so.1. It that simply do:
ln -s libgomp.so libgomp.so.1 in that directory. Maybe needs path or ./ before libgomp or the other way around. (see man ln)

---

### Post by arazgriz25 on 2014-05-11
Just for the record, I'm a bit of a linux noob, and i'm going on Tutorials and how tos.
:p

UPDATE: I tried ln -s libgomp.so.1 , didn't work, I'll try the variants to the command you gave.

---

### Post by MikeCyber on 2014-05-12
Well first where is it?
find / -name "*gomp*"
cd /to/that/dir
ln -s libgomp.so libgomp.so.1
but of course only if so.1 ist not there. You could also search with synaptic for the 
lib. Have a look at: man ln

---

### Post by arazgriz25 on 2014-05-18
> 
/var/cache/apt/archives/libgomp1-armel-cross_4.7.3-1ubuntu1cross1.81_all.deb
/var/cache/apt/archives/libgomp1-dbg_4.7.3-1ubuntu1_amd64.deb
/var/cache/apt/archives/libgomp1-dbg-armel-cross_4.7.3-1ubuntu1cross1.81_all.deb
/var/lib/dpkg/info/gcc-libgomp.list
/var/lib/dpkg/info/libgomp1:amd64.symbols
/var/lib/dpkg/info/libgomp1-armel-cross.shlibs
/var/lib/dpkg/info/libgomp1-dbg-armel-cross.list
/var/lib/dpkg/info/libgomp1:amd64.list
/var/lib/dpkg/info/gcc-libgomp.shlibs
/var/lib/dpkg/info/libgomp1-dbg:amd64.list
/var/lib/dpkg/info/libgomp1:amd64.postinst
/var/lib/dpkg/info/libgomp1:amd64.md5sums
/var/lib/dpkg/info/gcc-libgomp.md5sums
/var/lib/dpkg/info/libgomp1:amd64.shlibs
/var/lib/dpkg/info/libgomp1-armel-cross.postrm
/var/lib/dpkg/info/libgomp1-armel-cross.postinst
/var/lib/dpkg/info/gcc-libgomp.postinst
/var/lib/dpkg/info/libgomp1-armel-cross.md5sums
/var/lib/dpkg/info/libgomp1-dbg:amd64.md5sums
/var/lib/dpkg/info/libgomp1:amd64.postrm
/var/lib/dpkg/info/libgomp1-dbg-armel-cross.md5sums
/var/lib/dpkg/info/libgomp1-armel-cross.list
/var/lib/dpkg/info/gcc-libgomp.postrm
/usr/share/doc/gcc-libgomp
/usr/share/doc/libgomp1-armel-cross
/usr/share/doc/libgomp1
/usr/share/doc/gcc-4.7-base/gomp
/usr/share/doc/gcc-4.7-base/test-summaries/libgomp.sum.gz
/usr/share/doc/libgomp1-dbg
/usr/share/doc/libgomp1-dbg-armel-cross
/usr/arm-linux-gnueabi/lib/libgomp.so.1
/usr/arm-linux-gnueabi/lib/libgomp.so.1.0.0
/usr/lib64/libgomp.so
/usr/lib64/libgomp.so.1
/usr/lib64/libgomp.so.1.0.0
/usr/lib64/libgomp.a
/usr/lib64/libgomp.la
/usr/lib64/libgomp.spec
/usr/lib/debug/usr/arm-linux-gnueabi/lib/libgomp.so.1.0.0
/usr/lib/debug/usr/lib/x86_64-linux-gnu/libgomp.so.1.0.0
/usr/lib/gcc/x86_64-linux-gnu/4.7/libgomp.so
/usr/lib/gcc/x86_64-linux-gnu/4.7/libgomp.a
/usr/lib/gcc/x86_64-linux-gnu/4.7/libgomp.spec
/usr/lib/x86_64-linux-gnu/libgomp.so.1
/usr/lib/x86_64-linux-gnu/libgomp.so.1.0.0
/root/Ysflight/libgomp.so.1
/root/Ysflight/gcc-libgomp-4.8.1-1.ram0.98.x86_64.rpm
/root/Ysflight/gcc-libgomp_4.8.1-2_amd64.deb
That's what find gave me, which one do i go to? do i go to the one where libgomp.so.1 is, or somewhere else?

---

### Post by MikeCyber on 2014-05-19
The 32bit compat libs should help if you have a 32bit ysflight. Yes more likely it 
looks up /usr/lib32 for libgomp. So first of all you need to install compat libs and 32bit libgomp.
Make sure to install the 32bit compat libs (was ia32 or alike)

Well seems you're on a 64bit os that might not work with a 32bit app. Is that the 64bit version of the app?
Anyway you could do: - touch /etc/ld.so.conf.d/local.conf with only that line:

/usr/lib64

Then run the sudo ldconfig -v command.
The above only makes sure that if finds stuff within lib64. Might not be needed, so 
first of all I'd check what version of ysflight you have and if you can install that?

---

