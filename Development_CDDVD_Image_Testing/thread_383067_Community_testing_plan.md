---
title: "Community testing plan"
date: 2007-03-12
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-03-12
**We are now entering into an intensive period of testing, and this is where we really need your help!**

For the Alpha (Herd) releases we were mainly interested in checking that the ISO images were OK and find obvious bugs. Only a few distro team developers spent much time release testing the Alphas. For beta and beyond the distro team has traditionally spent a great deal of time doing testing, which could of course be better spent fixing bugs.

This time we have a chance to lighten that pressure through community-based testing, because of the great work we have already done in getting ourselves organised. However to get this right, the community testing effort must be tightly focused and coordinated so that it can be a reliable component of the test plan. This means focusing as a group on a few ISO images and tests.

Specifically we must consider:

**1. Reliability** - Planned tests have to get done. We can only release when we can confirm that all the test cases on all ISOs have been covered. And we want to release on time! 
**2. Turnaround time** - After one or more bugs in an ISO candidate has been fixed, that ISO must be built again and tested. The turn-around time on that can get quite tight as we get close to release, often just hours.[B]
3. Depth (quality of testing)[/B] - Assigned test cases must be known to get a certain level of testing (ideally the Long test program). When a test has been submitted, we must be reasonably sure that any serious bugs will indeed have been found.


The chance of getting these right with the community based testing is improved by focusing our efforts on a small number of ISOs and tests. With 5 or more testers signed up for a single test there is a good chance that it will get some testing fairly quickly. It also helps with the quality because each tester can spend more time on that one test. 

Based on what I've seen of testing in the forums, I suggest we aim for the following 6 tests:

```

 * i386, Ubuntu erase disk
 * i386, Ubuntu manual partitioning
 * i386, Ubuntu auto-resize
 * i386, Kubuntu erase disk
 * i386, Kubuntu manual partitioning
 * i386, Kubuntu auto-resize

```While doing any of these tests you should also do the CD check and live CD session. In addition, it would be good to test the WinFOSS on as many ISOs as possible because few core developers actually have Windows installs available.

** If you want to participate in this test run, please email iso.testing AT gmail.com with the following information:**

```

 * Forum and/or IRC nick
 * Launchpad ID (last part of URL)
 * Your primary test case [just one]
 * Secondary test cases
 * Whether you can do WinFOSS testing

```This address will be read by pochu and myself. We will try to coordinate so that we get the best possible coverage. We will likely ask people to adjust primary and secondary test priorities. It would also be good if you could give us a rough idea of known constraints on your time (like you'll be away on Monday, whatever).

I hope we can get good coverage on these so I can focus the distro team testing effort better as well (I happen to also be the person who assigns test cases to core developers). If we can prove that we are able to provide good test cover on these few tests for beta we can consider expanding the community contribution for the Release Candidate and Final (in fact, that would be a fantastic result!).

*ps. Please also do Edubuntu, Xubuntu and PowerPC testing, but coordinate that separately to this effort, which needs a tight focus. Thanks.*

---

### Post by fakie_flip on 2007-03-14
VMWare Server was working in Edgy. I upgraded to Feisty by running this.
```
gksu 'update-manager -d'
```
Now the VMWare Server module will not compile.

```
chris@ubuntu:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

chris@ubuntu:~$ sudo /usr/bin/vmware-config.pl 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-10-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-10-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-10-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

chris@ubuntu:~$ which gcc
/usr/bin/gcc
chris@ubuntu:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
chris@ubuntu:~$ dpkg -l | grep header
ii  linux-headers-2.6.17-10                    2.6.17.1-10.34                         Header files related to Linux kernel version
ii  linux-headers-2.6.17-10-generic            2.6.17.1-10.34                         Linux kernel headers for version 2.6.17 on x
ii  linux-headers-2.6.17-11                    2.6.17.1-11.35                         Header files related to Linux kernel version
ii  linux-headers-2.6.17-11-generic            2.6.17.1-11.35                         Linux kernel headers for version 2.6.17 on x
ii  linux-headers-2.6.20-10                    2.6.20-10.17                           Header files related to Linux kernel version
ii  linux-headers-2.6.20-10-generic            2.6.20-10.17                           Linux kernel headers for version 2.6.20 on x
ii  linux-headers-generic                      2.6.20.10.6                            Generic Linux kernel headers
chris@ubuntu:~$ cat /etc/issue.net 
Ubuntu feisty (development branch)

```

---

### Post by adamchri on 2007-03-14
First try sudo apt-get update and apt-get upgrade again - see if the new vmware-server-kernel modules comes along. If they don't download 'vmware-server-kernel-modules-2.6.20-10_2.6.20.3-10.9_i386.deb' from
[http://archive.ubuntulinux.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20](http://archive.ubuntulinux.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20)

and install with:

sudo dpkg -i vmware-server-kernel-modules-2.6.20-10_2.6.20.3-10.9_i386.deb

Worked for me on Feisty Herd4, kernel 2.6.20-10.

---

### Post by thiago e. de oliveira on 2007-03-14
The OpenOffice.org suite don't works. Its just open and close when I invoke.:confused: 

Any solution?:)

---

### Post by pochu on 2007-03-14
Please, stay on topic.

If you have a question, start a new thread.

---

### Post by Henrik on 2007-03-14
From the 10-11 email responses we are getting so far (thanks everyone!) it seems that Ubuntu manual partitioning is by far the most popular. I guess this is because people are installing it on systems with other OSes and prefer not to wipe the disk? Perhaps erase and auto-resize could be done on vmware?

I'm coordinating the results on [this page]("https://wiki.ubuntu.com/Testing/Commmunity") and have put up a short [FAQ]("https://wiki.ubuntu.com/Testing/Commmunity/FAQ"). The full test matrix with the devel team testers is [here]("https://wiki.ubuntu.com/Testing/Matrix") (CT is community testing; there is room for community growth!)

---

### Post by mixium on 2007-03-14
> **Henrik said:**
> From the 10-11 email responses we are getting so far (thanks everyone!) it seems that Ubuntu manual partitioning is by far the most popular. I guess this is because people are installing it on systems with other OSes and prefer not to wipe the disk? Perhaps erase and auto-resize could be done on vmware?

Yes, I will be using VMware player to assist with some of the tests. It is free as in beer btw.

> **Henrik said:**
>  I'm coordinating the results on [this page]("https://wiki.ubuntu.com/Testing/Commmunity") and have put up a short [FAQ]("https://wiki.ubuntu.com/Testing/Commmunity/FAQ"). The full test matrix with the devel team testers is [here]("https://wiki.ubuntu.com/Testing/Matrix") (CT is community testing; there is room for community growth!)

That is great news. Without receiving a reply to my offer to help testing I was left wondering if you had received it.

Michael

---

### Post by rtpca65 on 2007-03-14
Is the cant access tty problem going to fixed in this version?or is it my hardware

---

### Post by jtholmes on 2007-03-15
henrik

I posted what I believe are two serious
bugs in the ISO installer
One Crashes the Installer
my launch pad id is  jt-jtholmes

posted on  3/15/07
jt

---

### Post by Henrik on 2007-03-15
Hi jt,

Was that using ubuntu or Kubuntu? Odd that you didn't get an automated crash report upload for the crash in 92533. It doesn't have enough information to fix it as it now stands. See [info on uploading log files]("https://wiki.ubuntu.com/DebuggingUbiquity/AttachingLogs").

92531 also needs more information.

Btw, I'm locking this sticky thread. Let's continue elsewhere.

---

