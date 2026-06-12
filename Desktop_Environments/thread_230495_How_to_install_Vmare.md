---
title: "How to install Vmare"
date: 2006-08-06
forum: Desktop Environments
---

### Post by true_friend on 2006-08-06
I heard about vmare it is free and we can install windows in linux through it. please guide me to get and install vmare. is there any offical repository available???
or i have to download it manually.
seeking for instructions.
regards
True_Friend

---

### Post by usernamenone on 2006-08-06
download here.

[http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

instructions here.

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

when you get to this section:
2 Installing Required packages
 
You need to omit these
gcc-4.0-locales
gcc-4.0-doc

And should read like this instead:
apt-get install gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc libc6-dev-amd64 lib64gcc1

---

