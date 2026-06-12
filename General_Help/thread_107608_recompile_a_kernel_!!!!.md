---
title: "recompile a kernel !!!!"
date: 2005-12-23
forum: General Help
---

### Post by brakmaren on 2005-12-23
When installing vmware, i get the following message.'
----------
Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".
----------
I'm a total newbie, but not scared to mess things up.
But it woul'd be nice if someone coul'd give me some hints in
recompiling the kernel with gcc 4.0.2.
A step by step WOUL'D be nice ;-)
-----------
Found the HowTo.... sorry :-o
-----------
Maby it's enough to "restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5"."
I've found the 3.4 in apt-get. Is that enough, or do i HAVE to have the 3.4.5 ?
Any tips on where to find info on pointing the cc environment ???
Thank's
Anders

---

### Post by adie273 on 2005-12-23
Check out...

[http://www.ubuntuforums.org/showthread.php?t=77040&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=77040&highlight=vmware)

Hopefully it will help you out some.

Good Luck

Adie

---

### Post by rcerreto on 2005-12-23
Trying is a great attitude but in this case it should be a true waste of time.
Don't try compiling the kernel with gcc 4.0.2 you're going to fail.
Much better to compile the vmware module using gcc 3.4.
Just install it:
**sudo apt-get install gcc-3.4**

then remember to:
**export CC=/usr/bin/gcc-3.4**
before running vmware-config.pl

---

### Post by brakmaren on 2005-12-24
Searching on youre proposals lead me to
[https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29](https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29)
And that solved ALL problems.
Thank's fellows.

---

