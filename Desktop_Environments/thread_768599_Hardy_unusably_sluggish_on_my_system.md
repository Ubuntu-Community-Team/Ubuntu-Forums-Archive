---
title: "Hardy unusably sluggish on my system"
date: 2008-04-26
forum: Desktop Environments
---

### Post by akrapacs on 2008-04-26
I'm trying a new install on this desktop machine (specs below) and I have no problems during the install but afterwards when I boot into the system it's painfully sluggish. It can take up to 30 seconds to load the home folder in the file browser or to bring up a terminal window.

One thing I notice is at boot the splash screen with the activity indicator. When the activity indicator is in "indeterminiate" mode and the orange bar is just bouncing from side to side, it comes to an absolute crawl for about 3 to 5 minutes before returning to its normal pace and then switching to "determiniate" mode to show you the actual progress of the boot (meaning it's no longer bouncing from side to side it's representing a 0 - 100% value). The entire boot process takes well over 5 minutes. Note, I see the exact same behavior when I boot the live cd.

I've installed Hardy in a VM on my notebook and it runs flawless, so I understand it's something with my system, but I dont know what it is. Here are the specs:

Intel Pentium IV 2.23ghz
4GB RAM
ATI Radeon 9200 Video
Asus P4P800 Motherboard

Also, I'm using an 80GB hard drive partitioned with Windows XP n the first part of the partition, Hardy on the second, and an 8GB swap partition. I had the same setup with Gutsy installed and I didnt have the same problems. I'm installed right over top of Gutsy so this is not an upgrade.

---

### Post by blueturtl on 2008-04-26
Can you tell if a rogue process is eating up all the cpu cycles?

You can use the 'top' command in the terminal to do this (hit q to quit once done).

---

### Post by Linja on 2008-04-26
8GB of swap when you alread have 4GB or RAM :confused:

Anyway, you should run dmesg to find out what is going wrong while the system is booting. That sounds like a hardware issue, probably some driver.

---

### Post by akrapacs on 2008-04-26
I did check for a rogue process. When sitting idle there's nothing takeing any significant processor resources.

As for the swap, I'm still a little new to linux so when I was first installing a few months ago I read somewhere to use twice what your memory is for the swap file size. Could this possibly have a negative effect on a system?

Upon further investigation, you may be correct about a hardware or driver problem. When I attempted to start the system in recovery mode I noticed that there was one point during the startup where a step failed. It was during "Loading Hardware Drivers" and it said "error receiving the uevent message: No buffer space available".

I will look through the dmesg output to see if I can identify any problems.

---

### Post by akrapacs on 2008-04-27
I'm still not able to identify what the problem is here. I tried disabling and/or removing unnecessary hardware to see if I could produce any different results. It's currently taking over 10 minutes to boot up the system. 

I can't identify any problems in the dmesg output (which I have attached to this post). I'm really at a dead end right now. I even tried loading up kubuntu and xubuntu live cds and I see the same problems at bootup.

---

### Post by blueturtl on 2008-04-29
Did you succesfully run a previous version of Ubuntu on this hardware? Edit: Nevermind, checked your post. The following comments probably do not apply:

If not, have you considered loading setup defaults in the system BIOS or possibly upgrading the BIOS to a later version?

Intel systems also throttle a lot if the CPU temperature is too high so you may want to check that the cooling is functioning as supposed to.

--

You can try installing sysv-rc-conf via apt-get and disabling services that are unnecessary (for your system at least the nvidia-kernel might be one).

---

### Post by Carlos Fonseca on 2008-05-15
Hello akrapacs, looks like we have the same problem. I have a setup similar, same board and same amount of ram, and the only thing that made my ubuntu run ok was to take off 2 ram modules. Running with 2gb or ram made it run very fast.
It's very weird because I have windows XP in this machine too and it runs ok with 4gb of ram (recognizing 3.7gb, same as ubuntu anyway.)

---

