---
title: "Unable to boot!!!! (after succesfully installin ubuntu 10.04)"
date: 2010-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by captainapoorv on 2010-07-14
Hi, i have dell studio 1557 laptop..... i installed ubuntu today in 15GB partition /dev/sda5 (ext3) and have swap area of 5GB /dev/sda6 and i have 3 primary partitions from start......first is 40MB which is what i dont know and secong is RECOVERY of Windows 7 (15GB, dev/sda2) and third is Windows 7....................


what happened after installation was i rebooted and grub came up i selected ubuntu and it booted in to ubuntu i played for some time and then rebooted again and this time selected option "Windows (loader)" and it booted into windows then i shut down my laptop.......after a while i stared my laptop and it said "failed to find module" or something like that and then "No OS found"...... so i booted from live cd and checked things but cant get into it....again i installed ubuntu and it worked fine until i didnt boot into windows.........if i booted into windows it would work fine for 1 time then the same problem..........

guys please please help!!!!!!

---

### Post by jarviser on 2010-07-15
Are you sure you are not booting the recovery partition by mistake?  That would ruin the grub2 boot. 

I have a thinkpad with (1) the small system partition, (2) XP Recovery that Lenovo put there, (3) XP OS and (4) Ubuntu. They get along fine provided I never run the recovery . If I ever did I would need to reinstall Ubuntu (or fix the boot).

---

