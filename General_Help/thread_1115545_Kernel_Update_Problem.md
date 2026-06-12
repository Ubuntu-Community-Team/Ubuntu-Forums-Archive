---
title: "Kernel Update Problem"
date: 2009-04-03
forum: General Help
---

### Post by MobiusCoffee on 2009-04-03
EDIT:
I solved this by going to Synaptic Package Manager and just uninstaller the "kqemu-source" package.  Everything is okay now ^_^

I just updated Ubuntu Hardy after checking the "Pre-release Updates" in software sources.  Among the updates was a Kernel update and now there is a huge problem somewhere.  Most notably whenever I try to install anything.

```
~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  module-assistant libmp4v2-0 libxml++2.6c2a dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kqemu-source (1.3.0~pre11-8ubuntu1~hardy1) ...
 * Reloading kernel event manager...                                     [ OK ] 
Adding Module to DKMS build system

Error! DKMS tree already contains: kqemu-1.3.0~pre11
You cannot add the same module/version combo more than once.
Doing initial module build

Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
Installing initial module

Error! Could not locate kqemu.ko for module kqemu in the DKMS tree.
You must run a dkms build for kernel 2.6.24-19-generic (i686) first.
Done.
FATAL: Module kqemu not found.
 * Module kqemu failed to load
invoke-rc.d: initscript kqemu-source, action "start" failed.
dpkg: error processing kqemu-source (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kqemu-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I think it's trying to tell me what I should do, but I cannot understand it...  Please help.

edit:
if this is in the wrong section, would a moderator please move it to the correct one.

---

### Post by kevstar31 on 2009-04-03
you need to install **linux-source-2.6.24**

---

### Post by MobiusCoffee on 2009-04-03
Thank you!  I will try it out and post back with the results.

That did not work.  I can download the file, but when it tries to install the same error shows up.

edit:

solved

---

