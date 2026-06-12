---
title: "GRUB Fails on Reboot (Vista and Ubuntu) - Error 22"
date: 2009-01-17
forum: Desktop Environments
---

### Post by mundo01 on 2009-01-17
Here is the sequence of events that led to my current situation:

1. Installed on my Vista PC, 64 bit version of Desktop Ubunto. And things were kind of working fine. Except I could never the Ubuntu system to recognize my WiFi adapter.
2.  I read an article about an install within Windows called, Wubi, I decided to install Wubi with the expectation that it would help me correct my WiFi problem.
3. Once that the Ubuntu version of Wubi was up and running. I noticed that it was using something called Windows Boot Manager to start. However, because I also had the version of Ubuntu installed from step 1. When rebooting the GRUB loader would start, when I selected Vista as the Operating it would take me to the Windows Boot Manager from where I needed to select Vista or Ubuntu (Wubi installed version).  
4. Not knowing what I was doing, I decided within Vista to delete the erase the partition that contained the original (from step 1) Ubuntu. The result is that I must have also deleted the record that the GRUB loader is looking for as now the system fails during the GRUB loader process with error message 22.

How do I get correct this mess? :popcorn::lolflag:

---

### Post by caljohnsmith on 2009-01-17
How about booting your Vista Install CD, go to the command line and do:
```
bootrec /fixmbr
```
If you don't have a Vista Install CD, you can instead run the following from the Ubuntu install CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Let me know if that works or not, or if you run into problems.

---

### Post by mundo01 on 2009-01-18
I tried the sudo commands and it did not work. I just reinstalled Ubuntu and as a result GRUB and were created.  Now I need to uninstall GRUB and Ubuntu so I can use the Ubunt version I installed via Wubi.

---

### Post by frriction on 2009-05-19
I faced same problem about 6 months ago. I fond the iso file called supper-grub. I have download it and burn on CD, then boot from CD and it gives tool to fix the windows boot problem. 
I dont rememeber from where I downloaded it. Try to search supergrub.

---

