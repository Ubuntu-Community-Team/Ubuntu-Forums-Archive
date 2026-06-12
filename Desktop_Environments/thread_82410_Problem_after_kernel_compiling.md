---
title: "Problem after kernel compiling"
date: 2005-10-26
forum: Desktop Environments
---

### Post by RubenGonc on 2005-10-26
Hi you alll,

I've compiled myself a vanilla kernel with -ck patchset and made a package for it with make-kpkg.
Everything went fine until I reboot. In the boot progress I had an error:
> Mounting local filesystems     failed

What is the problem?Can anyone help me?

Thank you.

---

### Post by Kyral on 2005-10-26
99% of the time this means you forgot to compile in support for your device type (IDE and SATA) and/or your filesystem (ext2, ext3, Reiserfs, XFS, JFS, FAT32, etc)

What is the -ck patchset anyway?

---

### Post by HermanAB on 2005-10-26
Hmmm, see this guide:
[http://www.aerospacesoftware.com/kernel-compile-howto.html](http://www.aerospacesoftware.com/kernel-compile-howto.html)

Cheers,

Herman

---

### Post by Kyral on 2005-10-26
[quote=HermanAB]Hmmm, see this guide:
[http://www.aerospacesoftware.com/kernel-compile-howto.html]("http://www.aerospacesoftware.com/kernel-compile-howto.html")

Cheers,

Herman[/quote] Actually

[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto) 

is a very good resource :D

---

### Post by RubenGonc on 2005-10-26
Kyral it is a kernel with some patchs (con kolivas patched kernel):

[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

Thank you for reply...but it is strange as I used the default ubuntu .config (then doing some changes but no filesystems) :S

---

### Post by ranf on 2005-10-26
[QUOTE=Kyral]99% of the time this means you forgot to compile in support for your device type (IDE and SATA) and/or your filesystem (ext2, ext3, Reiserfs, XFS, JFS, FAT32, etc)
[/QUOTE]
Either that or he can make an initrd for his kernel (parameter `--initrd' on make-kpkg or with `mkinitrd').

---

### Post by Kyral on 2005-10-26
[QUOTE=RubenGonc]Kyral it is a kernel with some patchs (con kolivas patched kernel):

[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

Thank you for reply...but it is strange as I used the default ubuntu .config (then doing some changes but no filesystems) :S[/QUOTE]
Hmm

I wonder. Try compiling a vanilla kernel without the patches..I assume its the 2.6.13 kernel from Kernel.org...

---

