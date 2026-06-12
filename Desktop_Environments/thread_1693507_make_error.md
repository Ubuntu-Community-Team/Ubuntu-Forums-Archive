---
title: "make error"
date: 2011-02-22
forum: Desktop Environments
---

### Post by priyamvaidya on 2011-02-22
hello friends

i had installed ubuntu 10.10 on my harddisk partition.  i have upgraded to the latest kernel 2.6.37.

now i have to edit some .c files .  I edited the .c file in the appropriate directory.  after i did make it gave me error .   i am posting the full output that i am getting after running the make commands



[CODE
]root@priyam-desktop:/home/priyam/Desktop/coreutils-8.5 edited# make
make  all-recursive
make[1]: Entering directory `/home/priyam/Desktop/coreutils-8.5 edited'
Making all in lib
make[2]: Entering directory `/home/priyam/Desktop/coreutils-8.5 edited/lib'
make  all-recursive
make[3]: Entering directory `/home/priyam/Desktop/coreutils-8.5 edited/lib'
make[4]: Entering directory `/home/priyam/Desktop/coreutils-8.5 edited/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/priyam/Desktop/coreutils-8.5 edited/lib'
make[3]: Leaving directory `/home/priyam/Desktop/coreutils-8.5 edited/lib'
make[2]: Leaving directory `/home/priyam/Desktop/coreutils-8.5 edited/lib'
Making all in src
make[2]: Entering directory `/home/priyam/Desktop/coreutils-8.5 edited/src'
make  all-am
make[3]: Entering directory `/home/priyam/Desktop/coreutils-8.5 edited/src'
  CCLD     chroot
/usr/bin/ld: i386 86-64 architecture of input file `libver.a(version.o)' is incompatible with i386 output
collect2: ld returned 1 exit status
make[3]: *** [chroot] Error 1
make[3]: Leaving directory `/home/priyam/Desktop/coreutils-8.5 edited/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/priyam/Desktop/coreutils-8.5 edited/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/priyam/Desktop/coreutils-8.5 edited'
make: *** [all] Error 2
[/CODE]

the error it is giving me is this **"i386 86-64 architecture of input file 'libver.a(version.o)'** is incompatible with i386 output collect2:ld returned exit status.

i am not able to understand what is this error and how to resolve it.  it would be helpful if anybody could give me solution on how to resolve this error.

---

