---
title: "Very Broken Things (related to EFS encryption)"
date: 2009-03-25
forum: General Help
---

### Post by Greyhaven7 on 2009-03-25
I've scoured the Internet and have found and used several tools and methods to attempt to achieve my goal here... but have failed at every turn. From what I can tell from the sticky posts this is the appropriate forum (I'm not really sure). If not, please let me know.

[CENTER]**OK! Here's the low-down on what's happened so far. **[/CENTER]

I have a Compaq laptop. Said laptop has the whole hard drive partitioned as NTFS with **Windows XP Pro as the native OS**. 

**I used Wubi to install Ubuntu.** I managed to get the Broadcom card working with drivers in ndiswrapper. Once this had finished, it prompted me to download **262 updates** with the little icon on the menu bar. I clicked it and it started updating. I went back to surfing on  Firefox. 

A few minutes later the **computer locked up**. I could move the mouse but could not click anything, keyboard had no control either. 

I hard restarted the computer (held power button in for 5 sec). 

Upon turning the machine back on, **Ubuntu could not load up because Windows had the partition locked up** (something about **Kernel Panic**... I can look it up if more details are required). 

**Windows can not log in either**, it just continuously reboots, goes to the XP splash screen with the progress bar... and then restarts. I went into the options and told it not to reboot on system failures and found that it was popping an **0xC0000005 error**. 

I booted with the Ubuntu Live CD. Ubuntu could not mount the drive.

Windows Recovery Console won't let you use Extended ASCII chars (which are in my Administrator PW) so I used the Offline NT Password Reset boot disc to clear it. 

I **ran Windows Recovery Console**, which finished saying "complete" and that it had repaired some errors... although windows still won't boot up. 

Still couldn't get Windows to load up, but **Ubuntu live CD can now mount the drive**. (Ubuntu Wubi install is still throwing the Kernel Panic error at this point). 

I looked up the 0xC0000005 error and found that it can be caused by the software execution protection setting in **boot.ini**... so I went and fiddled with that through the Ubuntu live cd to no avail.

**[CENTER]***** Here is the main issue *****[/CENTER]**

[COLOR="DarkRed"]**I have files under another Windows username that are encrypted with Windows EFS encryption and can no longer access them. **[/COLOR]

I have:

[INDENT]* Access to The files (encrypted) via Ubuntu boot disc.
* The Username and Password that were used to encrypt them.
* Win XP CD
* Ubuntu CD
* Several other boot disc tools that I've used to attempt to restore this...[/INDENT]

I don't have:

[INDENT]* The Key (Certificate)
* Ability to actually log into windows in order to tell windows to decrypt them.[/INDENT]

Is there any Linux tool that can help me either decrypt the files or force windows to boot up so I can log in? 

I have another windows machine that I can use if anyone knows a tool/process that can achieve this.

---

### Post by cariboo on 2009-03-25
The only thing I can suggest, is did you run FIXBOOT and FIXMBR in the recovery console?

Jim

---

