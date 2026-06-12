---
title: "VMWare server install error"
date: 2007-07-17
forum: Desktop Environments
---

### Post by merrittr on 2007-07-17
Hi I am trying to install VMWARER server using vmware-install.pl 

and I get this ,  any ideas




make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

---

### Post by Twintop on 2007-07-17
What Ubuntu version are you running (and architecture)? You should be able to add

```

deb http://archive.canonical.com/ubuntu feisty-commercial main

```to your /etc/apt/sources.list file and download VMWare-Server through Add/Remove programs, Synaptic, or apt-get. You're going to need a VMWare-Server Serial Number any way you install, though. You can get one for free from VMWare's website if you haven't already.

See this link for more in-depth instructions on this method. This is what I've used for my 32-bit and 64-bit installs. [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.htm]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

---

### Post by zero244 on 2007-07-17
I had the same problem with vmware I had to download some dependencies before you try to install vmware. Once you do that vmware will complete the install.
Here is the How To I use
[http://linuxneophyte.com/install-vmware-server-on-ubuntu-edgy/](http://linuxneophyte.com/install-vmware-server-on-ubuntu-edgy/)

The latest version is 1.04 I believe which you need if your going to run it in Feisty.
Im using 1.03 with Edgy and it works fine. For one thing in version 1.03 and later they fixed a memory leak.
Good Luck hope the link helps.

---

### Post by Deco_21 on 2007-07-18
You need to look for the vmware patch for ubuntu . its call vmware-any-any-update109.tar.gz

---

### Post by veloce on 2007-07-18
> **zero244 said:**
> I had the same problem with vmware I had to download some dependencies before you try to install vmware. Once you do that vmware will complete the install.
Here is the How To I use
[http://linuxneophyte.com/install-vmware-server-on-ubuntu-edgy/](http://linuxneophyte.com/install-vmware-server-on-ubuntu-edgy/)

The latest version is 1.04 I believe which you need if your going to run it in Feisty.
Im using 1.03 with Edgy and it works fine. For one thing in version 1.03 and later they fixed a memory leak.
Good Luck hope the link helps.

I'm using 1.03 under feisty, as installed from the commercial repository suggested in previous post, why would I need 1.04?

---

### Post by zero244 on 2007-07-19
I couldn't get version 1.03 to work with Feisty and at that time version 1.04 wasn't out yet. So I actually went back to Edgy where version 1.03 works fine.
Also I have not been able to get Vmware to install properly without downloading a few dependencies before installing vmware.
Now maybe the dependencies are not needed with Feisty.
Did you finally get Vmware to work ok.

---

### Post by Dilz on 2007-07-20
merrittr -

I'm running in to the same problem, and Synaptic gives me some clues... when trying to install, it gives me this message:

vmware-server:
 Depends: vmware-server-kernel-modules  but it is not installable

I've added the appropriate repository, but no luck...

(deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main)

My n00b instinct tells me that this will be resolved, and that we should be patient when trying to use bleeding-edge software releases.

For the record, I'm using Gutsy Tribe 3 i386 on an AMD64-based system.

---

### Post by mooha on 2007-07-20
use virtualbox

---

### Post by Twintop on 2007-07-20
> **mooha said:**
> use virtualbox

Virtualbox is another good alternative, but is best suited for machines that have multiple cores AND hardware virtualization support. I have two Ubuntu boxes both running Feisty x86_64. One is a laptop with a Turion 64 ML34 1.8GHz (single core so no hardware virtualization), the desktop with an Opteron Santa Anna 1214 2.2GHz AM2 Dual Core (with hardware virtualization). Running Virtualbox on my desktop increases my CPU tempurature about 10-15F from 80F to 90-95F. On my laptop though, Virtualbox makes my CPU's tempurature goes from 105F to 170F or higher! VMWare on my laptop runs at about 130-135F with generally better performance.

Needless to say, it's Virtualbox on my desktop and VMWare on my laptop....

---

### Post by Dilz on 2007-07-20
> **mooha said:**
> use virtualbox

I gave VirtualBox a shot, and it works quite well. I am missing hardware virtualization, I believe, since I can't seem to get my VM to see my 3D card. I know very little about virtualization in general, so this may not be possible or easy to do...yet.

---

