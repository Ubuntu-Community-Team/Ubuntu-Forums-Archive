---
title: "[SOLVED] matlab installation help!"
date: 2007-10-07
forum: Education &amp; Science
---

### Post by miguelan on 2007-10-07
I've  been fighting quite a lot trying to install Matlab 7.04 on my laptop (x86_64 arquitecture).  I've read several threads and done my best finding information through Google. However, I cannot get matlab running.

Basically, the installation proceeds quite fine, i.e. no errors at all, I copy both license files, I replace $HOSTNAME by that of my computer, etc. When running matlab for the first time I get the following error:
"*** glibc detected *** /usr/local/matlab/bin/glnxa64/MATLAB: malloc(): memory corruption: 0x0000000000598320 ***",
which I  solved by adding the following two lines to the .matlab7rc.sh file:
LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL

But after doing all these operations I still get the following error:
"expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

    Sorry! We could not determine the machine architecture for your
           host."

Does anybody out there know how to solve this issue? Is there anybody that successfully installed matlab on a x86_64 machine and who might explain me step by step how to do it?

Thanks in advance,


Miguel

---

