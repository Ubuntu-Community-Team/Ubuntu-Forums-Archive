---
title: "&quot;Unable to start services for VMware Tools&quot;"
date: 2009-05-28
forum: General Help
---

### Post by Astlarya on 2009-05-28
I've searched many threads in various forums and none of the solutions seem to work for me, so I hope I'm not being an idiot here by bringing it up in a new thread, but here's my problem:

I have VMware Fusion 2.0.4 and Ubuntu 9.04 Jaunty inside of that, and I'm on a Macbook Pro. I've been trying to install VMware Tools so that I can drag-and-drop files from Ubuntu to Leopard like I do between Leopard and Windows XP (inside VMware as well). However, it seems to be a slightly more complicated process with Ubuntu.

I followed the instructions to run ./vmware-install.pl and follow all the defaults, but I came up with a few kernel modules I had to remove first. "vmci", "vmmemctl", "vmxnet", and "vmblock". So, I removed those with the "rm /lib/modules/2.6.28-11-generic/misc/ModuleName.{o,ko}" command and continued on.

Everything seemed to be going fine- and I accepted all the defaults- installing the vmware tools until the end when it simply said, "Unable to start services for VMware Tools [...] Execution aborted." I'm wondering if it has to do with the VM communication interface socket family showing "failed" or what's the deal. I'm definitely new to Linux, and the whole thing is a learning process. :) But if anyone has any suggestions, I'd be most appreciative.

P.S. I'm also wondering, based on my research into other threads, if it is VMware not keeping up to date with the current Ubuntu build. But I have no clue.

I'll paste my Terminal segment below...

```
root@Maddie-ubuntu:~# /usr/bin/vmware-config-tools.pl

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
   Virtual Printing daemon:                                            done
   VM communication interface socket family:                           done
insserv: warning: script 'S20linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'K01gdm' missing LSB tags and overrides
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'S02powernowd.early' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 2 3 5 6) of script `vmware-tools' overwrites defaults (0 6).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'powernowd.early' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (1) of script `nvidia-kernel' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: current stop runlevel(s) (1) of script `ufw' overwrites defaults (empty).
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 1 6) of script `apport' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (1) of script `policykit' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-11-generic/build/include] 

Extracting the sources of the vmmemctl module.

/bin/tar: /usr/lib/vmware-tools/modules/source/vmmemctl.tar: Cannot open: No such file or directory
/bin/tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-tools/modules/source/vmmemctl.tar" file in
the "/tmp/vmware-config25" directory.

The memory manager driver (vmmemctl module) is used by VMware host software to 
efficiently reclaim memory from a virtual machine.
If the driver is not available, VMware host software may instead need to swap 
guest memory to disk, which may reduce performance.
The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you want the memory management feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config26/vmhgfs-only'
make -C /lib/modules/2.6.28-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /tmp/vmware-config26/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/backdoorGcc64.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/cpNameLite.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/dentry.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/dir.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/file.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/filesystem.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/fsutil.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/hgfsBd.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/hgfsEscapeLinux.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/hgfsUtil.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/inode.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/kernelStubsLinux.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/link.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/messageBackdoor.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/message.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/module.o
  CC [M]  /tmp/vmware-config26/vmhgfs-only/page.o
/tmp/vmware-config26/vmhgfs-only/page.c: In function ‘HgfsDoWriteBegin’:
/tmp/vmware-config26/vmhgfs-only/page.c:763: warning: ISO C90 forbids mixed declarations and code
/tmp/vmware-config26/vmhgfs-only/page.c: In function ‘HgfsWriteBegin’:
/tmp/vmware-config26/vmhgfs-only/page.c:867: error: implicit declaration of function ‘__grab_cache_page’
/tmp/vmware-config26/vmhgfs-only/page.c:867: warning: assignment makes pointer from integer without a cast
make[2]: *** [/tmp/vmware-config26/vmhgfs-only/page.o] Error 1
make[1]: *** [_module_/tmp/vmware-config26/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config26/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 
None of the pre-built vmxnet modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmxnet module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmxnet module.

/bin/tar: /usr/lib/vmware-tools/modules/source/vmxnet.tar: Cannot open: No such file or directory
/bin/tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-tools/modules/source/vmxnet.tar" file in 
the "/tmp/vmware-config27" directory.

The fast network device driver (vmxnet module) is used only for our fast 
networking interface. The rest of the software provided by VMware Tools is 
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils, 
make and the kernel sources for your running kernel are installed on your 
machine. These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

None of the pre-built vmblock modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmblock module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Extracting the sources of the vmblock module.

/bin/tar: /usr/lib/vmware-tools/modules/source/vmblock.tar: Cannot open: No such file or directory
/bin/tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-tools/modules/source/vmblock.tar" file in 
the "/tmp/vmware-config28" directory.

The vmblock module enables dragging or copying files from within a host and 
dropping or pasting them onto your guest (host to guest drag and drop and file 
copy/paste).  The rest of the software provided by VMware Tools is designed to 
work independently of this feature (including guest to host drag and drop and 
file copy/paste).

If you would like the host to guest drag and drop and file copy/paste features,
you can install the driver by running vmware-config-tools.pl again after making
sure that gcc, binutils, make and the kernel sources for your running kernel 
are installed on your machine. These packages are available on your 
distribution's installation CD.
[ Press Enter key to continue ] 

[EXPERIMENTAL] The VMware FileSystem Sync Driver (vmsync) is a new feature that
creates backups of virtual machines. Please refer to the VMware Knowledge Base 
for more details on this capability. Do you wish to enable this feature? 
[no] 

None of the pre-built vmci modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmci module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmci module.

/bin/tar: /usr/lib/vmware-tools/modules/source/vmci.tar: Cannot open: No such file or directory
/bin/tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-tools/modules/source/vmci.tar" file in the
"/tmp/vmware-config29" directory.

The communication service is used in addition to the standard communication 
between the guest and the host.  The rest of the software provided by VMware 
Tools is designed to work independently of this feature.
If you wish to have the VMCI feature, you can install the driver by running 
vmware-config-tools.pl again after making sure that gcc, binutils, make and the
kernel sources for your running kernel are installed on your machine. These 
packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 



Detected X.org version 7.5.0.



No drivers for X.org version: 7.5.0.



Do you want to change the starting screen display size? (yes/no) [no] 


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Maddie-ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/vmware-config30/XF86ConfigLog.19694", Time: Thu May 28 02:23:35 2009
(++) Using config file: "/tmp/vmware-config30/XF86Config.19694"
Parse error on line 13 of section Files in file /tmp/vmware-config30/XF86Config.19694
    Ignoring obsolete keyword "RgbPath".
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

X is running fine with the new config file.

 ddxSigGiveUp: Closing log
   Checking acpi hot plug                                              done
Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   VM communication interface socket family:                          failed
   Guest operating system daemon:                                      done
   Virtual Printing daemon:                                            done
Unable to start services for VMware Tools

Execution aborted.
```

---

