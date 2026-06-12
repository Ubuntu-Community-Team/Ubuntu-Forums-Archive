---
title: "Command syntax help"
date: 2006-01-15
forum: General Help
---

### Post by bikeboy on 2006-01-15
Hey guys I'm trying to use the mkntfs command to format a partition as ntfs. I have gotten the latest version of ntfsprogs working fine but I can't work out the syntax for one of the options.

I have tried this but it doesn't work.

> sudo mkntfs -n -w 3.1 -p 366 /dev/sda2 9117

If I remove the "-w 3.1" part it works fine so that must be where the problem lies. In the man pages it says:

> mkntfs [ options ] device [ number-of-sectors ]

mkntfs [ -C ] [ -c cluster-size ] [ -F ] [ -f ] [ -H heads ] [ -h ] [ -I ] [ -L volume-label ] [ -l ] [ -n ] [ -p part-start-sect ] [ -Q ] [ -q ] [ -S sectors-per-track ] [ -s sector-size ] [ -T ] [ -V ] [ -v ] [ -w ntfs-version ] [ -z mft-zone-multiplier ] [ --debug ] device [ number-of-sectors ]

-w STRING
--ntfs-version STRING
Select the version of NTFS you wish to use. This can be one of "1.2", "3.0", or "3.1".

Im not sure how to enter the argument when it needs to be a STRING. I have also tried using "3.1" , %3.1 and %"3.1", everything I can think of. The same thing happens with another option that requires a string argument so I know it's my syntax.

How should I be doing it?

Thanks

---

