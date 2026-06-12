---
title: "GCC8 for Linux Kernel 4.18.8"
date: 2018-09-22
forum: Desktop Environments
---

### Post by sheenlim08 on 2018-09-22
Hello,

I'm new to the community and opted in with Xubuntu as my main desktop environment and have my Windows as a VM.
I use VMWare Workstation 14.1.3 for my VM and part of the requirement is GCC 7 under the default kernel in Xubuntu (Kernel v4.15) which worked fine.

I then used UKUU to update my Linux Kernel to the latest available for my desktop which is v4.18.8 which was successful, then when I ran VMWare Workstation it required GCC8 (It required GCC8 when using Kernel v4.18.8, but required GCC7 when using Kernel v.16.18). I then tried to install the  "gcc-8-x86-64-linux-gnu" but it can't be installed. It shows this result.

sheenlim08@HP-Z820-Xubuntu:~$ sudo apt-get install gcc-8-x86-64-linux-gnu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gcc-8-x86-64-linux-gnu:i386 : Depends: libgcc-8-dev-amd64-cross:i386 (>= 8-20180414-1ubuntu2cross1) but it is not installable
E: Unable to correct problems, you have held broken packages.

Any help is appreciated, I am not able to find any documentation for GCC8 about its kernel requirements so I switched back to the highest Kernel version that allows me to use GCC7 which is v4.16.18.

---

### Post by Doug S on 2018-09-22
I do not understand your GCC version verses kernel version requirements, because as far as I know they aren't dependent (within reason).
I can only assume that your issue is related to the relatively new kernel configuration parameter "CONFIG_GCC_VERSION" which recently changed from 70300 to 80200 for Ubuntu kernels.
You could try compiling the kernel yourself, as it seems that when you do that parameter will automatically get set to whatever GCC version you are using to compile the kernel (in my case 5.4 (50400):

```
doug@s15:~/temp-k-git/linux$ scripts/diffconfig .config-4.19.0-041900rc3-lowlatency .config
-CC_HAS_SANCOV_TRACE_PC y
-DEBUG_INFO_DWARF4 y
-DEBUG_INFO_REDUCED n
-DEBUG_INFO_SPLIT n
-GDB_SCRIPTS y
-KCOV n
-XEN_SCRUB_PAGES y
 DEBUG_INFO y -> n
 [COLOR="#FF0000"]GCC_VERSION 80200 -> 50400[/COLOR]
+EROFS_FS n
+XEN_SCRUB_PAGES_DEFAULT y

```

EDIT: In my opinion the root issue here is not "why cann't I install GCC version 8?", but rather "why is vmware, or whatever, complaining about which version of GCC I have?"

---

### Post by sheenlim08 on 2018-09-27
Sorry for the late reply,

Correct, I believe that ultimately i have a problem with GCC version 8 installing on the latest Kernel.
[ATTACH=CONFIG]281202[/ATTACH]

Any ideas on what action I can take to install GCC8?

---

### Post by oldos2er on 2018-09-28
What does ```
sudo apt-get build-dep gcc-8-x86-64-linux-gnu
``` yield?

---

### Post by monkeybrain20122 on 2018-09-29
On my ubuntu 18.04

```
sudo apt install gcc-8
[sudo] password for monkeybrain
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm6.0:i386
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  cpp-8 libasan5 libgcc-8-dev libubsan1
Suggested packages:
  gcc-8-locales gcc-8-multilib gcc-8-doc libgcc1-dbg libgomp1-dbg libitm1-dbg
  libatomic1-dbg libasan5-dbg liblsan0-dbg libtsan0-dbg libubsan1-dbg
  libmpx2-dbg libquadmath0-dbg
The following NEW packages will be installed:
  cpp-8 gcc-8 libasan5 libgcc-8-dev libubsan1
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.0 MB of archives.
After this operation, 69.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
n
```

But after installation you have to make it your default with update-alternatives
[https://askubuntu.com/questions/26498/how-to-choose-the-default-gcc-and-g-version](https://askubuntu.com/questions/26498/how-to-choose-the-default-gcc-and-g-version)

---

