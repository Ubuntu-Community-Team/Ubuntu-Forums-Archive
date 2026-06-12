---
title: "I guess EXT4 is starting to bite me!"
date: 2009-06-24
forum: General Help
---

### Post by kpkeerthi on 2009-06-24
Ubuntu froze completely twice so far - while the package updates were being installed, a few weeks back and today morning, while I was rsync'ing the files to my backup drive. 

**_My Partition Layout:_**
/ - EXT4
/boot - EXT2
/home - EXT4
Backup drive - JFS

I recovered using the Magic SysRq (Alt + SysReq + R E I S U B) and then fsck'ing the partitions; no data loss. 

I suspect the freeze could be due to EXT4 since it froze while Ubuntu was busy accessing hard disk, both the times. Is there any log that I could check to find out if it was EXT4 so I could send it to the devs?

---

### Post by Primefalcon on 2009-06-24
Question: are you running an ATI graphics card?

---

### Post by LoloftheRings on 2009-06-24
What if you put some extra volts (not safe to do) on your cpu or degrease your frequency (safe to do)?
This has been my problem for a long time until I bought a new cooler for my cpu.

---

### Post by kpkeerthi on 2009-06-24
> **Primefalcon said:**
> Question: are you running an ATI graphics card?

No. nvidia.

---

### Post by kpkeerthi on 2009-06-24
> **LoloftheRings said:**
> What if you put some extra volts (not safe to do) on your cpu or degrease your frequency (safe to do)?
This has been my problem for a long time until I bought a new cooler for my cpu.

Well, this is on a laptop. If I'm correct it's not possible on laptops. In any case, I do not want to mess with my hardware and I'm too poor to afford another one should something go wrong.

---

### Post by kpkeerthi on 2009-07-18
I could consistently reproduce the issue with the stock Jaunty kernel [2.6.28]: I created a test folder in my $HOME and mirrored my entire / (root) in it. I ran **sudo rm -rf ~/test/root/** and Jaunty froze completely. 

Today I compiled the latest stable kernel (2.6.30.1) from source, ran the test. Surprisingly Jaunty did not freeze. I immediately booted with the stock kernel and could reproduce it. I'm now relieved as I was worried if the freeze was due to my hardware.

---

