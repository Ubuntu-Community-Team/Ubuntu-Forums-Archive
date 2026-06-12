---
title: "Slow IO"
date: 2009-01-19
forum: General Help
---

### Post by malfist on 2009-01-19
I have a SATA II Harddrive and I was talking to my boss at work and I told him I was averaging around 30-35 MiB/S write speeds on my hard drive. He told me that that is really slow and that I should be seeing 60-70 instead. 
I am running fully encrypted but the benchmarks online show that there is only a 1-3MiB/s difference between encrypted and non-encrypted systems.

Here's Bonnie++'s output:
```

jerome@ubuntu-desktop:~$ bonnie++ -n 256
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
ubuntu-desktop   8G 36239  64 38955   8 18130   3 37040  60 36300   2 141.2   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                256 18195  26 +++++ +++  8048   9 57842  82 +++++ +++  6295   7
ubuntu-desktop,8G,36239,64,38955,8,18130,3,37040

```

Anybody know what's going on and how I can fix it?

Edit: System specs
4 GB RAM
AMD Phenom 9850 Black (2.5GHz quad)
250GB Sata II (WD?)
750GB Sata II Hatachi (not used in the test, only a backup drive)
200GB IDE WD (not used in the test, windows drive, rarely used)

Edit II: All HDD's are 7200RPM, no RAID.

---

