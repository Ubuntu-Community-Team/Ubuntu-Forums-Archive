---
title: "Wanted: Partitioning Scheme Ideas"
date: 2006-05-08
forum: Desktop Environments
---

### Post by bpont on 2006-05-08
OK...so I got myself a nice, new 250 gig hard drive that I will add to my system this week.

I have windoze 98 on my first hard drive and will put Ubuntu, Gentoo, and LFS on the second hard drive on seperate partitions, of course.  I want to create one big (100 gig?) partition that would be FAT32 to keep my content (music, video, other personal stuff, etc.), so it's accessible under whichever OS I'm using at the moment.

I want to create the largest partition for Ubuntu (which will be my main OS as much as possible...will hold off and do clean install of Dapper when it - hopefully - comes out next month), then I will install Gentoo on maybe a 20 or 30 gig partition and LFS (Linux From Scratch) on a 10 gig partition.  I'm basically using Gentoo and LFS as systems to learn on and get better skills / understanding, etc.  How big should I make my Ubuntu partition?  Remember I'll be keeping my 'stuff' on the FAT32 partition, so I really only need space for the base system and any addition applications I add on over time...obviously, I will need 'breathing room' on the partition to add applications and update the system.

I'm thinking with 512mb of physical memory, I'd carve out 1 gig of swap space, but not sure if I should have a single 1 gig swap partition or multiple smaller ones and don't know how to have a system mount multiple swap partitions (guessing it's an fstab issue)

Any and all advice will be great appreciated...thanks Ubuntu Brothers and Sisters.

---

### Post by tonyr on 2006-05-08
I gave Ubuntu 6.4G, based on my past experiences with other distributions and my
mix of apps, which is not too extensive at the moment.  For Dapper purposes,
everything is on one partition, even my home directory (currently ~200Mb).
The partition is about half full at this point (or half-empty, depending on
you point of view).

It really depends on what your apps are going to be.  My clean installation
approached 2G.

This is only one sample point, of course. *Caveat emptor*, YMMV, etc etc.

---

### Post by Jungingen on 2006-05-08
[QUOTE=tonyr]I gave Ubuntu 6.4G, based on my past experiences with other distributions and my
mix of apps, which is not too extensive at the moment.  For Dapper purposes,
everything is on one partition, even my home directory (currently ~200Mb).
The partition is about half full at this point (or half-empty, depending on
you point of view).

It really depends on what your apps are going to be.  My clean installation
approached 2G.

This is only one sample point, of course. *Caveat emptor*, YMMV, etc etc.[/QUOTE]

My partitioning (i have to discs)
HDA:

0,5Gb Ext3FS /   +boot flag

0,5Gb Ext3FS /tmp

1,0Gb Ext3FS /home

2,5Gb Ext3FS /var

4,5Gb Ext3FS /usr

31,0Gb FAT32 /media/games
HDB:

5,0Gb NTFS /media/backup (for Windows instalation) +boot flag

16,0Gb FAT32 /media/install (for files to use linux and windows)

1,0Gb SWAP (Linux swap)

If you want to get more speed from ubuntu, you need to mount partition like that

---

### Post by matthewstory on 2006-05-08
personally I would go like this (just for ubuntu):

Mount Point:          Size:               FLAGS:                          FS

/boot                      100MB            boot, read only               ReiserFS
/tmp                       500MB                                                ReiserFS
/var                        3GB                                                    ReiserFS
/var/log                   500MB                                                ReiserFS
/var/tmp                  500MB                                                ReiserFS
/usr/local                 2GB                                                   ReiserFS
swap                       1GB                                                   swap
/                              50GB                                                 EXT3
shared files              150GB                                               FAT32
Windows                  8GB                                                  NTFS
Gentoo                     20GB                                                (various)
LFS                          14.4                                                  (various)

---

