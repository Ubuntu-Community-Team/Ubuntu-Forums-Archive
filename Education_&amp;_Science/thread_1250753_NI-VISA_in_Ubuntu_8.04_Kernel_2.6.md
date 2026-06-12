---
title: "NI-VISA in Ubuntu 8.04 Kernel 2.6"
date: 2009-08-26
forum: Education &amp; Science
---

### Post by buster2209 on 2009-08-26
Has anybody had any luck getting NI-VISA working with LabVIEW 8.5 on Ubuntu Hardy? 

I have LabVIEW running flawlessly but NI-VISA just wont install!!

I have had it working before but can't seem to get it to work again!!!!

I'm using Linux Kernel 2.6

---

### Post by buster2209 on 2009-08-26
This is the message I get when trying to install NI-VISA in Ubuntu Hardy;

 

The following components will be installed using rpm:
  NI-VISA Runtime 4.2.0              3199 KB  (in /usr/local/vxipnp)
  NI-VISA Development 4.2.0          9303 KB  (in /usr/local/vxipnp)
  NI-VISA Configuration 4.2.0         524 KB  (in /usr/local/vxipnp)
  NI-VISA Server 4.2.0                250 KB  (in /usr/local/vxipnp)
  PXI Services 1.6.0                  791 KB  (in /usr/local/natinst/nipxi)
  NI Spy 2.5.1                       2286 KB  (in /usr/local/natinst/nispy)
  CVI Runtime 8.0                    8554 KB  (in /usr/local/natinst/cvirte)
  LabVIEW Runtime 8.2.1             38472 KB  (in /usr/local/lib/LabVIEW-8.2)
  NI-ORB 1.7.0                        481 KB  (in /usr/local/natinst/.nicore)
  NI-DIM 1.7.0                        585 KB  (in /usr/local/natinst/.nicore)
  NI-RPC 3.4.0                        123 KB  (in /usr/local/natinst/.nicore)
  NI-PAL 2.1.0                       1843 KB  (in /usr/local/natinst/nipal)
  NI-KAL 1.6.0                        237 KB  (in /usr/local/natinst/nikal)
Total space required:               66648 KB
Space available:                164092588 KB

Continue? [Yn] y

Installing selected components ...

error: Failed dependencies:
    **kernel >= 2.4.0 is needed by nikali-1.6.0-f0.i386**
    /bin/sh is needed by nikali-1.6.0-f0.i386
    /bin/sh is needed by nipali-2.1.0-f1.i386
    /bin/sh is needed by nirpci-3.4.0-f1.i386
    /bin/sh is needed by niorbi-1.7.0-f0.i386
    /bin/sh is needed by nidimi-1.7.0-f0.i386
    /bin/sh is needed by nipxirmi-1.6.0-f0.i386
    ld-linux.so.2 is needed by nipxirmi-1.6.0-f0.i386
    libdl.so.2 is needed by nipxirmi-1.6.0-f0.i386
    libc.so.6(GLIBC_2.0) is needed by nipxirmi-1.6.0-f0.i386
    libc.so.6(GLIBC_2.1) is needed by nipxirmi-1.6.0-f0.i386
    libc.so.6(GLIBC_2.1.3) is needed by nipxirmi-1.6.0-f0.i386
    libc.so.6(GLIBC_2.2) is needed by nipxirmi-1.6.0-f0.i386
    libdl.so.2(GLIBC_2.0) is needed by nipxirmi-1.6.0-f0.i386
    libdl.so.2(GLIBC_2.1) is needed by nipxirmi-1.6.0-f0.i386
    libpthread.so.0(GLIBC_2.0) is needed by nipxirmi-1.6.0-f0.i386
    libpthread.so.0(GLIBC_2.1) is needed by nipxirmi-1.6.0-f0.i386
    /bin/sh is needed by nicvirte-8.0-6.i386
    /bin/sh is needed by labview82-rte-8.2.1-2.i386
    /bin/sh is needed by nivisa-4.2.0-f1.i386
    /bin/sh is needed by nivisa-devel-4.2.0-f0.i386
    /bin/sh is needed by nivisa-config-4.2.0-f0.i386
    /bin/sh is needed by nivisaserver-4.2.0-f1.i386
    /bin/sh is needed by nispyi-2.5.1-f0.i386

Running NI-KAL Post Installation Script ...

 
Configuring for linux kernel version 2.6.24-24-generic.
 
********************************* NOTE *********************************
Using kernel headers found in /lib/modules/2.6.24-24-generic/build.
If this does not correspond to the location of the 2.6.24-24-generic headers,
then define KERNELHEADERS in your environment to point to the location
of the kernel headers, define KERNELTARGET as the version of the
kernel for which to compile, and then rerun ./configure.
********************************* NOTE *********************************
 


Does NI-VISA work on kernels > 2.4?

---

### Post by Keen101 on 2009-08-29
I havent tried it yet myself, but for the rest of LabVIEW i installed them by converting the .rpm packages with ALIEN to .deb packages. If you convert the NI-VISA packages with ALIEN they might install...

---

### Post by buster2209 on 2009-08-31
> **Keen101 said:**
> I havent tried it yet myself, but for the rest of LabVIEW i installed them by converting the .rpm packages with ALIEN to .deb packages. If you convert the NI-VISA packages with ALIEN they might install...

I tried that but two of the created .deb packages wouldn't install, however, I found another way;

[NI-VISA 3.0]("http://joule.ni.com/nidu/cds/view/p/id/232/lang/en") is the latest version that works on Ubuntu Hardy 8.04

For future reference;

1 - Download the .TZ and install file from the link above and place them in the same folder

2 - Navigate to the folder via Terminal and type "sudo bash ./install" and follow the instructions

3 - Once it's installed, type "sudo visaconf" to configure NI-VISA 

4 - :guitar:  Happy Days!!!

---

### Post by Dyqik on 2009-10-09
You can get around the dependency problems by running the INSTALL script with INSTALL --nodeps

However that is not the final hurdle.  There are a number of posts on the NI forums about getting this to work, but I haven't yet found a definitive procedure.  I'm trying a number of tricks at the moment (just installing Karmic beta to a virtual machine to try some out on the newest LTS release).

Paul

---

