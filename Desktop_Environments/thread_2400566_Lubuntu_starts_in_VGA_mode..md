---
title: "Lubuntu starts in VGA mode."
date: 2018-09-07
forum: Desktop Environments
---

### Post by lgbowden on 2018-09-07
Why has my Lubuntu system/server started rebooting in VGA mode?

---

### Post by Autodave on 2018-09-07
What version of Lubuntu are you running?  Did it ever run properly? What video card are you using?  Desktop or laptop?

---

### Post by lgbowden on 2018-09-07
Welcome to Ubuntu 16.10 (GNU/Linux 4.8.0-59-generic i686)

Linux version 4.8.0-59-generic (buildd@lcy01-25) (gcc version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) ) #64-Ubuntu SMP Thu Jun 29 19:37:59 UTC 2017

LXDE.

It's always worked.

VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rage 128 PRO Ultra AGP 4x

Desktop Compaq AP550 2 x P3 1GB RAM. 2 x optical and 1 x AIT drive.

PCI/SATA for mdadm RAID.

System is still working as a server but screen is now VGA when it was SVGA.

---

### Post by ajgreeny on 2018-09-07
Ubuntu 16.10 has not had any support since July 2017 so I'm afraid we will not be able to give you any useful help with your problem as the repos for 16.10 have been moved and have had no updates since that date.

You should update to a fully supported version; I recommend a clean install of 18.04.1, and you can not run an online update to 18.04 as it would require three separate actions, 16.10 - 17.04, 17.04 - 17.10, and finally 17.10 - 18.04.  That would be a very long process and has, in my opinion, far too many opportunities for problems to occur.

---

### Post by lgbowden on 2018-09-08
"and has, in my opinion, far too many opportunities for problems to occur." is Linux in a nutshell. Nobody really gives a damn that a system that has been running for years with no changes just suddenly stops working. And yet leaving it completely alone has also presented "opportunities for problems to occur". How? Why? As a home user all my PC's used to be dual boot but it was always Linux that gave me issues so slowly but surely, as they've been replaced, they're no longer dual boot. Windows wins. In fact this Lubuntu problem system is the final remaining Linux system in the house. I'm not paid to do this so why should I spend hours and hours on this one system on something that is so banal as a screen that worked for years correctly now no longer does - despite my best endevours. So. As a server it is still working which gives me some time. FreeNAS maybe as an intermediate solution and then an external network enabled disk caddy.

---

### Post by ajgreeny on 2018-09-08
I'm sorry that Linux appears not to have worked for you but there really is no point in anyone attempting to help you continuing to use 16.10 versions of any of the *ubuntu family of OSs; it would be a bit like attempting to make sure that everything in Windows XP was still up to date and secure, which is of course, no longer possible for the same reasons that 16.10 can not be made secure.

If, as you say, Windows wins for you, that is fine; we do not gain anything by persuading computer users to use Linux/Ubuntu instead of Windows if they can not get it to do what they need but there is no answer, other than updating to a supported version, that we can give you any magic answer to your problem.

---

### Post by lgbowden on 2019-05-29
Ironic you say this as MS have just launched an update for XP. Even more ironic is that yesterday, with no changes made by me apparently, this Lubuntu system was rebooted and it booted back into SVGA mode after the best part of a year in VGA mode.

---

### Post by cruzer001 on 2019-05-29
[https://www.microsoft.com/en-ww/windowsforbusiness/end-of-xp-support](https://www.microsoft.com/en-ww/windowsforbusiness/end-of-xp-support)

---

### Post by Autodave on 2019-05-29
Maybe it isn't even a software issue: have you checked the connections between the PC and the monitor?

I find it hard to believe the MS just did an update for XP since we have known for quite awhile that Win7 will no longer receive updates next year.

AND, you paid for Windows!  11 machines here running Xubuntu 14.04, 16.04, and 18.04 and not a glitch with any of them.

---

