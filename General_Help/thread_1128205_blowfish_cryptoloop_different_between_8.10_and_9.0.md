---
title: "blowfish cryptoloop different between 8.10 and 9.04rc ?"
date: 2009-04-17
forum: General Help
---

### Post by thoughtbox on 2009-04-17
I have a blowfish encrypted filesystem which I created in 8.04 (amd64) 
which has functioned fine after upgrading to 8.10 (amd64). In these two
releases I used:

  sudo modprobe loop
  sudo modprobe blowfish
  sudo modprobe cryptoloop
  sudo losetup -e blowfish /dev/loop0 /media/bfish0
  sudo mount -t ext3 /dev/loop0 /media/bfish0

When I use the same 5 steps in 9.04, the first one fails, but this should
be ok as it appears that 'loop' is already compiled into the kernel 
(2.6.28-11-generic):

  $ dmesg loop0|grep loop:
  [    1.221121] loop: module loaded

The mount command fails, however:

  sudo mount -t ext3 /dev/loop0 /media/bfish0
  mount: wrong fs type, bad option, bad superblock on /dev/loop0,
         missing codepage or helper program, or other error
         In some cases useful info is found in syslog - try
         dmesg | tail  or so

I've double-checked that I have used the correct passphrase (obvious 
mistake), and also fired up a 32-bit 8.10 Live CD to ensure that it is
not the blowfish.img that is damaged (I am able to mount the filesystem
and read/write data to it).

Can someone clue me in on what has changed? What should I use instead?

Thanks.

/TB

---

