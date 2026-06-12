---
title: "Install latest Jack"
date: 2009-01-14
forum: General Help
---

### Post by ussndmac on 2009-01-14
Hi,

Not sure this is the right forum, but here goes:

Since I need(want) features (namely alsa_in/out) in Jack 116 and Ubuntu Studio comes with 109 I need to build the latest.

The following is from the FAQ at [www.jackaudio.org](www.jackaudio.org) with my questions mixed in:

---------------
[I]Prerequisites
    * 2.4, 2.5 or 2.6 series kernel with tmpfs turned on (CONFIG_TMPFS)[/I]

Ok, so I have 2.4 from the Ubuntu Studio, but how do I determine if tmpfs is turned on?


[I]    * Shared memory file system mounted on /dev/shm. add the following to /etc/fstab to get it mounted at boot:

      	shmfs       /dev/shm     shm    defaults        0       0

            (Note: you may have to make the /dev/shm directory)
[/I]

Ok, so /dev/shm exists, but is mounted as devshm already. Adding the above and rebooting shows no errors in any log that I found, but only devshm shows up when I "mount -l"


[I]Once you have the correct shmfs support, you should be able to build jack with the following sequence of commands:

sh ./autogen.sh
./configure
make
make install
[/I]

Obviously these get typed in a terminal session. But:
[LIST]
[*]as root?
[*]what directory should I be in?
[*]where do I extract the tar ball that has the source?
[/LIST]

Haven't done anything like this in a UNIX like system since the late 1980's...so the gray cells are a bit rusty.;)

---

