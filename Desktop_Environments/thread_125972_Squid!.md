---
title: "Squid!"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Castrum on 2006-02-05
hi,
OS:Kubuntu 5.10

i have download Squid (squid-2.5.STABLE12-20060205) and i want install.But doesent work , 
i put in Terminal "sudo apt-ge t install squid",then i recieve this message: :root@ubuntubadjo:/home/blazenko/Desktop/squid-2.5.STABLE12-20060205# "sudo apt-ge t install squid"
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package squid

I try with :"./configure" and i recieve this message:
[email]root@ubuntubadjo:/home/blazenko/Desktop/squid-2.5.STAB[/email]LE12-20060205# ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler (gcc  -g) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

Can somone tell me what's the problem?

cheers

Castrum

---

### Post by Connollyir on 2006-02-05
I think you might need to recheck your repositories and or the server containing the squid .deb is down. It looks to me like the last half of your message failed because not all the packages for squid were installed. Make sure you have the Universe and Multiverse repositories enabled and try it again, but keep in mind the server could be down also.


-Ian

---

