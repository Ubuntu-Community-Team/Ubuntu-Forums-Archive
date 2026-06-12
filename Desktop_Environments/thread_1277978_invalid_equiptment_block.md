---
title: "invalid equiptment block"
date: 2009-09-29
forum: Desktop Environments
---

### Post by GoldenSun on 2009-09-29
Ok so I oc'd my system and had it running stable 24/7 for like 6 months straight.  I decide to oc my ram and cpu some more for fun.  I do nothing major, nothing boots so I set it back to the previous stable oc.  

Now when I boot I get a black screen that says this...

error: invalid environment block
Failed to boot default entries.
Press any key to continue...

I press and key and it just repeats those lines over and over again.  

I shut computer off, take out cmos battery to reset bios.  Boot back up and same thing happens.  

Take a stick of ram out, same thing.  Did it with the other stick also.

Inserted a live cd, ran memtest 86+ on both sticks.  All pass with no errors.
Still same screen.  

I insert a live cd and I can boot with the cd...  

Any ideas on how to fix this??

System:
AMD Athlon64 x2 4850e @ 3.0 ghz, 1.35 vcore
Biostar TA790GX
G.Skill value ram (2x2gb) 800 5-5-5-15, 1.9v
Corsair 400w 80+

---

### Post by kellsens on 2009-09-29
I'm with the same problem. I hope that somebody have some ideas.

---

### Post by GoldenSun on 2009-09-29
Solved:
ran fdsk and all that stuff, no  problems.  

What I had to do was boot with live cd.  Mount my hd under /mnt and bind /dev /proc /dev/pts.  
I had to purge grub-pc and grub-common and remove the /boot/grub/ folder.  Then I installed the regular grub package.  
Then ran grub-install /dev/sda.  

Rebooted and it through me into a grub shell.
then did
root (hd0,0)
kernel /vmlinuz root=/dev/sda1 ro
boot

once in I did a sudo update-grub

This was caused by a bad ram oc which corrupted the grub2

I'm posting this on a few other forums because there is absolutely no solutions to this problem as of yet.

---

### Post by kellsens on 2009-09-30
Thank you very much! This solution help me a lot.

---

### Post by Prometheus7 on 2009-10-02
I did not OC any portion of my system and I am getting this same error. If you think this was due to a corrupted RAM stick, why didn't the memtest return an error?

I am running memtest, afterwards I will try to update grub. Is there any way to do what you did using the alternate install disk?

---

### Post by Prometheus7 on 2009-10-02
I didn't have any errors found with the memtest. It is odd that we all had the same problem at the same time. I was unable to do a fresh install of grub (after purging) so I am reinstalling the OS right now.

I've got to wonder: Could this be the result of some other issue (perhaps from a recent Karmic update)?

UPDATE: [http://swiss.ubuntuforums.org/showthread.php?p=8027504]("http://swiss.ubuntuforums.org/showthread.php?p=8027504")

---

### Post by the_tom on 2009-10-04
I had also the same problem and I found that there was allready a [Bugreport]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784") in Launchpad. In Comment #2 there is a temporary solution which worked for me.

---

### Post by Tteddo on 2009-10-05
> **the_tom said:**
> I had also the same problem and I found that there was allready a [Bugreport]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784") in Launchpad. In Comment #2 there is a temporary solution which worked for me.

I did #11 to get it to boot, then did #2. Managed to do that before the Beta ISO downloaded!
This happened to me immediately after installing all the updates to karmic today, so it must have been the update to grub2 that I saw go by.

---

