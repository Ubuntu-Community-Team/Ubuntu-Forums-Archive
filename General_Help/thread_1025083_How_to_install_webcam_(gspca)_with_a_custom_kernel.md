---
title: "How to install webcam (gspca) with a custom kernel? Is there a guy that managesthat ?"
date: 2008-12-29
forum: General Help
---

### Post by frenchn00b on 2008-12-29
Hello, 

I installed a new kernel this way:
```
wget -N http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.8.tar.bz2
cd /usr/src
tar xjf linux-2.6.27.8.tar.bz2
cd linux-2.6.27.8
make menuconfig
#make dep
make-kpkg clean
#make-kpkg kernel_image
make-kpkg --revision=custom-rev03 kernel_image
ls 
echo "compiling done , install"
ls
echo "done, type enter install" 
read kjklfskljfds
dpkg -i kernel-image-2.6.27.8_i386.deb
```


I would like to install the gspca for my webcam but no way.
```
aptitude install gspca-source
m-a prepare
m-a a-i gspca
modprobe gspca
 modprobe gspca
FATAL: Module gspca not found.
```

```
usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        Modules.symvers
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
rm -f *.symvers
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        Modules.symvers
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27.8/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27.8/g ;s/#KVERS#/2.6.27.8/g ; s/_KVERS_/2.6.27.8/g ; s/##KDREV##/2.6.27.8-10.00.Custom/g ; s/#KDREV#/2.6.27.8-10.00.Custom/g ; s/_KDREV_/2.6.27.8-10.00.Custom/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27.8 KERNELDIR=/lib/modules/2.6.27.8/source
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /lib/modules/2.6.27.8/source SUBDIRS=/usr/src/modules/gspca CC=gcc-4.1 modules
make[3]: Entering directory `/usr/src/linux-2.6.27.8'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-2.6.27.8'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2
```

---

### Post by fragos on 2008-12-30
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by frenchn00b on 2008-12-30
> **fragos said:**
> [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Thanks but the problem is in the kernel. Where ?

Are you good in compiling kernels, well very good? I have questions about this gpsca ... :( :( :( :)

---

### Post by fragos on 2008-12-30
I've never had the need to compile a kernel. All I can say is this guy probably knows more about webcam drivers than anyone else on this planet.

---

### Post by frenchn00b on 2008-12-30
> **fragos said:**
> I've never had the need to compile a kernel. All I can say is this guy probably knows more about webcam drivers than anyone else on this planet.

there is the v2 of gspca but still it didnt work on my machine (yet :( ) :
[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

tahnk you!!

---

