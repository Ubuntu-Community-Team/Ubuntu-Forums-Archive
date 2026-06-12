---
title: "RealPlayer/ia32-libs issue in Jaunty 64-bit"
date: 2009-06-11
forum: General Help
---

### Post by notfound123 on 2009-06-11
I am running RealPlayer 11 on Jaunty 64 (followed these instructions to install [https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods))

I get: 
xxx@xxx-laptop:~$ realplay
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

I did some searching online and it appears to be a bug in ia32-libs. Is this correct? Is there a workaround? The ia32-libs that I have is 2.7ubuntu6.

Thanks.

---

### Post by kuja on 2009-06-11
Maybe you can grab the lib you need with the getlibs script. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by notfound123 on 2009-06-12
Ended up installing 32-bit version of Jaunty back. 64-bit version is sooo buggy...  Back to 32 and everything (RealPlayer included) just works without any tweaking.

(Can someone please move this to "x86 64-bit Users" section?)

---

