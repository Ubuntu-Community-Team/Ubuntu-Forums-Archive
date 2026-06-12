---
title: "its unveliebable"
date: 2005-11-04
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-04
i spent almost a day downloading virtual machine VNware and this is what i got after an installing procedure


Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.3". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.3", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".
  

does anyone have a clue about this.

10x in advanced

---

### Post by MartinG on 2005-11-04
You need to install GCC-3.4 (it's in the repositories) and ensure you point to it. (The quick and dirty fix is to fiddle with the symlink in /usr/bin to point to it). If I recall correctly, to use VMWare tools you will also need g++ if it's not already installed.

---

### Post by MrCheese on 2005-11-04
[QUOTE=mxyzptlk]i spent almost a day downloading virtual machine VNware and this is what i got after an installing procedure


Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.3". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.3", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

does anyone have a clue about this.

10x in advanced[/QUOTE]

First install gcc-3.4.5, backup the vmware-config.pl file then it looks as simple as looking for the definition of gcc in /usr/bin/vmware-config.pl and hard-coding it to your gcc version. eg.  you will probably find something like "CC=" and some environment variable stuff pointing to the kernel-build compiler, change it to CC=<the path for gcc-3.4.5>.

Sorry to be a bit vague but it just requires a bit of tinkering on your part.

---

### Post by nuggien on 2005-11-04
install gcc 3.4 from synaptic...then before running the vmware config perl script, 

do 
[PHP]export CC="/usr/bin/gcc-3.4"[/PHP]

then run the config script...

---

### Post by mxyzptlk on 2005-11-04
well now i'm stuck here: 


What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


i installed all you told me and also did the php code.

sorry i feel frustrated.


samba doesn work to me and now virtual machine neither, i have four days almost without sleep and im tired but i have to make this working and then i have to make a report to my boss if Linux is reliable or no.

I know it is but he doesnt (hehe) till now no sharing printers and folders and anything, and i have to build a network with three XP boxes one mac and two printers.     That network configuration is working with XP.

well thanks for any suggestion

---

### Post by VR6Pete on 2005-11-04
Follow this:

[http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware)

---

### Post by mxyzptlk on 2005-11-04
well still stuck in the same even with that wizzard

same message

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/bin" is an existing directory, but it does not contain at least
one of these directories "linux", "asm", "net" as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

any other idea

---

### Post by Zwack on 2005-11-04
ls /usr/src/linux*  Choose the one that matches your kernel....

I would use /usr/src/linux-headers-2.6.12-9-k7

I hope that this helps,

Z.

---

### Post by mxyzptlk on 2005-11-04
well it seems that none of the kernels i have, matches with the kernel my system was compiled (wierd isn't it)

# whereis kernel
kernel: /usr/src/linux-headers-2.6.12-9-686/kernel /usr/src/linux-headers-2.6.12-9/kernel

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9/include

The directory of kernel headers (version 2.6.12-9) does not match your running
kernel (version 2.6.12-9-386).  Even if the module were to compile successfully,it would not load into the running kernel.


What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9-686/include

The directory of kernel headers (version 2.6.12-9-686) does not match your
running kernel (version 2.6.12-9-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


so those are the messages i got


any suggestion

10x in advanced

---

