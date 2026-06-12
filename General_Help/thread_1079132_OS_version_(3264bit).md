---
title: "OS version (32/64bit)"
date: 2009-02-24
forum: General Help
---

### Post by CR34M3 CR4CK3R on 2009-02-24
Hi,
I'm a new user to Ubuntu (intrepid) and I would like to know if it's possible to check whether I've installed the 32bit or 64bit version? I don't recall specifying it during the install.
Thanks :)

---

### Post by bumanie on 2009-02-24
In terminal type > uname -a It will list the kernel version, followed by the Os version x86_64 means you have a 64bit OS, x86_i386 (I think it is) means a 32bit OS.

---

### Post by CR34M3 CR4CK3R on 2009-02-24
Using the uname command, I get this:

andre@mimir:~$ uname -a
Linux mimir 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:35 UTC 2009 i686 GNU/Linux

Does the i686 architecture imply a 64bit ubuntu installation?

---

### Post by mb_webguy on 2009-02-24
No, that's 32-bit.

You aren't given the option of whether to install 32- or 64-bit Ubuntu during installation.  They're different installation CDs.  If you'll notice on the [download page]("http://www.ubuntu.com/getubuntu/download"), below the Download button there's an option to select whether you want 32- or 64-bit.

---

### Post by CR34M3 CR4CK3R on 2009-02-24
Ah, thanks. :)

---

