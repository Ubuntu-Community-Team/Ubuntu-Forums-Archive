---
title: "Benchmarking HDD Performance"
date: 2009-05-17
forum: General Help
---

### Post by kamasabi on 2009-05-17
Hey ya'll,

I finally got around to putting my new server together, and looking for some benchmarks I could run in regards for read / write reports on my drives.  I have already run hdparm for general read performance and ran bonnie, however, I was curious as to if there was a graphical report that anyone knew of or something that would create a general synopsis of the disk performance (Something a little easier to look at).

The current configuration is 6 1TB WD hard drives in a RAID 5 configuration, quad core processor and 4GB of memory (across 2 sticks).

Here is the report from those two:

```

HDD Test Report

kamasabi@LianLi:~$ bonnie
Writing with putc()...done
Writing intelligently...done
Rewriting...done
Reading with getc()...done
Reading intelligently...done
start 'em...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version 1.03c       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
LianLi        6552M 52637  96 91898  23 76469  19 59556  96 319302  47 216.6   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
LianLi,6552M,52637,96,91898,23,76469,19,59556,96,319302,47,216.6,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++
kamasabi@LianLi:~$ 



kamasabi@LianLi:~$ sudo hdparm -Tt /dev/md1
[sudo] password for kamasabi: 

/dev/md1:
 Timing cached reads:   2840 MB in  2.00 seconds = 1420.25 MB/sec
 Timing buffered disk reads:  894 MB in  3.00 seconds = 297.74 MB/sec
kamasabi@LianLi:~$ 

```

---

