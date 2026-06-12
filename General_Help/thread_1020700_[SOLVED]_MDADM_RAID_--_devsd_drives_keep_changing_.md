---
title: "[SOLVED] MDADM RAID -- /dev/sd** drives keep changing on reboot!"
date: 2008-12-24
forum: General Help
---

### Post by joeinbend on 2008-12-24
Hi all,
I have been making myself familiar with MDADM, for managing/creating RAID arrays, and I love it! The only problem I am stumped on is, when I reboot, sometimes the order of the /dev/sd** drives will change, so my array fails to mount. I have to go into the partition manager to see which is which (I just check to see which /dev/sd** is the actual system drive, everything else is part of the RAID), then I have to go edit my  /etc/mdadm/mdadm.conf and update the devices= list to reflect the change. then, i can remount the array, restart samba, and I'm good again.

Problem is, this is unacceptable! I'm sure there is a straightforward way to resolve this, but I have not found an answer. Any ideas out there?

EDIT: Forgot to mention, the big killer is that after remounting the RAID, it is in degraded mode, because of the missing drive, and when I sudo mdadm /dev/md0 -a /dev/sd(x) to add the drive back in, it takes several hours to rebuild, during which time the array is not fault-tolerant, and will be completely lost if I should sustain an actual drive failure during that time. Help!

---

### Post by ibuclaw on 2008-12-24
My advice would be not to use the /dev/sd* locations then.

I know in fstab, you can use the UUIDs of the hard drives to identify which is which to ensure that the exact same drive is mounted everytime.

Is this possible with mdadm?

I will have to look into it first...

Regards
Iain

---

### Post by joeinbend on 2008-12-24
This sounds like the way to go - I have never done this before, can you give me a quick and dirty guide on doing this?

---

### Post by joeinbend on 2008-12-24
This has been solved. I found that the problem was, I upgraded from the apt-get version of mdadm, I believe v2.6.3, to the latest, v2.6.8, to resolve some known issues. The way that is prescribed to do it is to uninstall the current version (apt-get purge...) then Make, Make Install the new one from source. The problem is, it doesnt "register" for lack of the correct term, when you do it this way, so functions such as "dpkg-reconfigure mdadm" report that no such package is installed. hmmmm! so, I reinstalled from the repository (sudo apt-get install mdadm) which put the v2.6.3 back on, then I just did the Make and Make Install over the top of that, to load v2.6.8. This worked, and "sudo mdadm --version" reports the new version. Since then, all volumes remain where they're supposed to, and auto assemble and mount upon booting Ubuntu. What a relief! 

I must note: This is a newbie's fix. I am pretty sure that building from source after Purging the old version is actually the correct way, but I do not know much more than copying/pasting other's solutions as far as fighting my way thru Linux, so I dont know how to fix this intelligently. If anyone can offer a "REAL" solution, I'm all ears! And I know others are too, because google'ing around with this problem, many have had the same problem as I.

---

### Post by dcstar on 2008-12-24
> **joeinbend said:**
> This has been solved. I found that the problem was, I upgraded from the apt-get version of mdadm, I believe v2.6.3, to the latest, v2.6.8, to resolve some known issues. The way that is prescribed to do it is to uninstall the current version (apt-get purge...) then Make, Make Install the new one from source. The problem is, it doesnt "register" for lack of the correct term, when you do it this way, so functions such as** "dpkg-reconfigure mdadm" report that no such package is installed. hmmmm!** so, I reinstalled from the repository (sudo apt-get install mdadm) which put the v2.6.3 back on, then I just did the Make and Make Install over the top of that, to load v2.6.8. This worked, and "sudo mdadm --version" reports the new version. Since then, all volumes remain where they're supposed to, and auto assemble and mount upon booting Ubuntu. What a relief! 


Packages installed outside of the apt system mean that the apt system knows nothing about them, and it cannot manage them in any way.

The only reason you "solution" worked is that you re-installed the package with apt, then over-wrote the binaries with the make install. As far as apt is concerned, you still have the original package installed.

---

