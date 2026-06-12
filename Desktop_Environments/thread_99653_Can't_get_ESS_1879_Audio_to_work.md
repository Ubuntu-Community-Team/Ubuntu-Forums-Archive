---
title: "Can't get ESS 1879 Audio to work"
date: 2005-12-06
forum: Desktop Environments
---

### Post by virbonus on 2005-12-06
I'm a linux newbie but have spent about 50 hours trying to resolve this problem online so any help would be much appreciated.

I'm running Breezy Badger and have a Sony PCG 505TR which has a built in ESS-1879 Audio chipset. I saw a post in the Hoary Hedgehog forums that suggested one first do a 

killall esd
which returns:
esd: no process killed

It was then suggested that I do a lsof /dev/dsp, the output of which is shown below.

rlr@ubuntu:~$ lsof /dev/dsp
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
lsof: status error on /dev/dsp: No such file or directory
lsof 4.75

I would guess that nothing is loading but I don't know what files to look in. 

If anyone can direct me where to start I'd sure appreciate it.

---

### Post by waffen on 2005-12-06
Check this: [http://ubuntuforums.org/showthread.php?t=99000](http://ubuntuforums.org/showthread.php?t=99000)

---

### Post by virbonus on 2005-12-06
Thanks but so far a no-go

---

