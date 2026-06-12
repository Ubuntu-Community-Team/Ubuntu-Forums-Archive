---
title: "Partitioner Problem (Solved!)"
date: 2005-10-14
forum: Desktop Environments
---

### Post by hmgp on 2005-10-14
Hi all. I'm not new to Linux. I love it. I was a Fedora guy until I experimented with Ubuntu (4.10). Since then it's what I recomend to every friend.

Now my problem: First time I'm installing in a Laptop. I have a Toshiba Satellite Pro 4270. It has a new Fujitsu HD with 30Gb. 
With 5.04 everything is OK I can use the partitioner, but with 5.10 the installer hangs at 52% of "Starting up the partitioner".

Help anyone?

Many thanks.

---

### Post by hmgp on 2005-10-14
Well. I've been trying parameters to the kernel but no luck.

So I tried one thing, I started with 5.04 and partitioned the disk with, since I knew it worked. Then hard stoped the instalation of 5.04.

Turned off Laptop. Changed the CD to the 5.10 and ... it worked!!!!!
The partitioner in the 5.10 worked fine from there on.

Strange, no doubt about it. I know it wasn't a solution, it was only a workaround, but I had to do the install ...

---

### Post by aysiu on 2005-10-14
Sounds as if 5.04 was a bum CD or corrupt image. Glad it all worked out for you, though.

---

### Post by fif on 2005-10-22
Not sure it was a cd burning problem. I have exactly the same problem with a samsung VM7000. Partitioner hangs up also at 52% exactly...

I'll try your trick hmgp, but needs to download 5.04 first.

---

### Post by recce101 on 2005-10-22
[QUOTE=fif]Not sure it was a cd burning problem. I have exactly the same problem with a samsung VM7000. Partitioner hangs up also at 52% exactly...
I'll try your trick hmgp, but needs to download 5.04 first.[/QUOTE]

Almost ditto here. I've been using 5.04 with excellent results, have installed it many times using various options, always without any problems. It's the only distro I've tried which detects all my hardware every time on both machines. But I've never managed to get 5.10 through the install routine. I tried the "rc" release and got the hangup you described, so decided to wait for the "real" 5.10 which was official a week or so ago. Same thing, hung at the partitioner step at exactly 52% every time. This is on a homebuilt system with 1gb AMD processor.

So here's what I'm going to try: Prepare a new ext3 partition with either 5.04 or PartitionMagic (I already have a swap partition), then start the 5.10 installation but at some point use the "go back" feature to bypass the 5.10 partitioning sequence. Is this essentially the method that worked for you? I'll let you know how it goes.

---

### Post by recce101 on 2005-10-22
[QUOTE=recce101]So here's what I'm going to try: Prepare a new ext3 partition with either 5.04 or PartitionMagic (I already have a swap partition), then start the 5.10 installation but at some point use the "go back" feature to bypass the 5.10 partitioning sequence. Is this essentially the method that worked for you? I'll let you know how it goes.[/QUOTE]
Well, no go on that. Regardless of which "go back" item I choose, it insists on re-entering the partitioning sequence with the resultant hang-up, sometimes at 52%, other times a bit later. Right now I'm downloading the Kubuntu 5.10 release to try. I usually just do the "server" install anyway, then add packages selectively to arrive at a lean XFCE configuration.

---

### Post by fif on 2005-10-22
hmgp trick worked for me. I installed 5.04 and 'savagely' stopped the computer after the successful partitionning, i.e. as soon as installation of packages started on the partitionned disk. Note that I let the partitionner use the complet hard disk.
HTH

---

### Post by recce101 on 2005-10-22
[QUOTE=recce101]Well, no go on that. Regardless of which "go back" item I choose, it insists on re-entering the partitioning sequence with the resultant hang-up, sometimes at 52%, other times a bit later. Right now I'm downloading the Kubuntu 5.10 release to try. I usually just do the "server" install anyway, then add packages selectively to arrive at a lean XFCE configuration.[/QUOTE]
That didn't work either. The Kubuntu 5.10 hung at exactly the same place -- 52% loading the partitioner. I'm downloading the live version now to see if that loads okay. If not, I guess it's 5.04 for the next 6 months.

---

