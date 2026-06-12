---
title: "Truecrypt help"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Bonez56 on 2006-07-26
Hi all,

I installed truecrypt following a HOWTO on these forums, and everything was working fine.

At the time, I was running the standard i386 kernel that ships with Ubuntu.

Since then i've installed the linux-k7 package which is a more suitable kernel for my AMD CPU.

Now, whenever I try to mount volumes with truecrypt I get an error about the kernel module being the incorrect version.

So, I downloaded the truecrypt source tarball and compiled it myself from scratch, using the linux-source-2.6.15 package from aptitude.

This is what happens now when I try to mount a volume:

```


blake@bonezpc:~/Desktop/truecrypt-4.2a/Linux$ sudo truecrypt /d/volume /mnt
Enter password for '/d/volume':
truecrypt: Incorrect version of kernel module loaded - version 4.2 required
blake@bonezpc:~/Desktop/truecrypt-4.2a/Linux$

```

Can anyone tell me where i've gone wrong and how I can get it to work again? 

Thanks
Bonez

---

### Post by gborzi on 2006-07-26
Did you compiled truecrypt 4.2 and used this version for crypting your partition ? If so, it seems that 4.2a is not backward compatible, which is very strange. Or perhaps the installation script replaced the kernel module but not the truecrypt binary. You may try > sudo <path for the compiled truecrypt binary>/truecrypt /d/volume /mnt
to see if this is the problem.

---

### Post by mike984 on 2006-07-26
I am getting the same error.  Although I have never been able to get it to work.  I downloaded the Ubuntu 6.06 version from the Truecrypt website and I've also tried the one located at [http://www.savefile.com/files/1316093](http://www.savefile.com/files/1316093)  I am using the latest linux-686 version.

Anyone have any suggestions?  I would really like to see if I can get this program to work.

---

### Post by gborzi on 2006-07-26
The precompiled truecrypt packages have only one module, generally compiled for the i386 kernel, so it doesn't work with the k7 kernel. Moreover, these packages may have been compiled against some kernel version prior to the latest update. I have compiled successfully truecrypt 4.2 on my AMD Athlon XP 2800+ and on my Pentium M laptop, and now I'm using it. I have not updated to 4.2a because it took too long to compile.
In case you need truecrypt soon, I'm attaching to this post a .tar.bz2 archive with the truecrypt kernel module, binary and manpage. Put the kernel module in /lib/modules/2.6.15-26-k7/extra/ change the owner (of the module) to root, and run *sudo depmod -a*. Put the binary and the manpage in the appropriate locations (e.g. /usr/local/bin and /usr/local/man/man1 respectively) and see if it works.

---

### Post by Bonez56 on 2006-07-27
Thank you so much for your kind help, it worked a treat!!

Cheers
Bonez

---

