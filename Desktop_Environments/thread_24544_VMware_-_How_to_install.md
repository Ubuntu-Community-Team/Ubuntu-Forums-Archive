---
title: "VMware - How to install?"
date: 2005-04-07
forum: Desktop Environments
---

### Post by Promethe on 2005-04-07
I'm trying to install VMware, but I can't. After nearly all installing, on the end, I've got such info: ```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is an existing directory, but it does not
contain at least one of these directories "linux", "asm", "net" as expected.

```
What can I do with it? I've downloaded and extracted linux kernel from respositories, and in "include" directory there are "linux", "asm" and "net" directories.
What should I do? I've got latest k7 kernel and latest default kernel.

---

### Post by bored2k on 2005-04-07
Download your linux-headers (linux-headers-k7 ; linux-headers-2.6.11-1-k7 , etc [what suits yours kernel]).

Also get build-essential if you haven't.

---

### Post by freelsjd on 2005-04-07
I had similar problems.  I went back to building my own kernels as I have always
done under Debian. Also remove all Ubuntu-supplied kernels. Then build my own kernel with module support with all required supporint packages. Then and only then could I get vmware install to build the vmware modules correctly. vmware 4.5.2 is working fine here with ubuntu + 2.6.11.6 or 2.4.29 kernels.

---

### Post by vvu on 2005-04-07
Using Kubuntu 5.04 Preview with all latest updates...

freelsjd - did you apply the fix recommended by Ubuntu FAQ - this page -->  [http://www.ubuntulinux.org/wiki/VMware](http://www.ubuntulinux.org/wiki/VMware) -- this is the only thing that fixed it for me.  However, I did not rebuild any kernels.  Why would rebuilding kernel fix it and not require this fix?  Sorry...still kind of new to Linux.

---

### Post by freelsjd on 2005-04-07
I acknowledge that was the only link I could find on vmware using a search for vmware of the entire ubuntu web site. However, that was not the problem. The problem has to do with vmware needs to build the vmware modules based on the header files that correspond to the presently running kernel. So, basically, as long as the header files match the running kernel, then the vmware modules will run. Most of the "commercial" distributions have presupplied vmware modules that can be downloaded from vmware as it is installed or installed from the vmware install package. However, in the case of Debian, and now Ubuntu, there are not preexisitng vmware modules so they must be compiled. I tried installing all the companion header files, build packages, etc. that recommended that are available under Ubuntu. None of this seemed to work. So, after wasting a couple of hours trying to get it working the Ubuntu way, I gave up and resorted to the way that I knew would work.

What I suggest, since Ubuntu is now very widely used, is to make available pre-compiled vmware modules either on the Ubuntu servers or the vmware servers. This same type problem exists with the Nvidia drivers and other proprietary modules (such as Cisco vpn modules for example). 

Don't let compiling your own kernel scare you or keep you from using these very good products.  It is not difficult.

---

### Post by minio on 2005-04-07
I get vmware to work on ubuntu :grin: 
So i think you should change
/usr/src/linux/include 
to
/lib/modules/yourkernel/build/include
at least it works for me.

---

### Post by Promethe on 2005-04-08
Sorry, I didn't wrote, then I think about VMware 5, not 4.5
After installing linux-headers works fine
Whoa!! It's much faster then real XP and Longhorn!

---

### Post by bored2k on 2005-04-08
[QUOTE=Promethe]Sorry, I didn't wrote, then I think about VMware 5, not 4.5
After installing linux-headers works fine
Whoa!! It's much faster then real XP and Longhorn![/QUOTE]
 Are you serious? vmware 5 is that good?

---

### Post by Promethe on 2005-04-08
Yes! It works VERY fast (on VERY fast machine of course) but remember, then Longhorn hasn't god SB16 driver, so U need to seek for it :]

---

