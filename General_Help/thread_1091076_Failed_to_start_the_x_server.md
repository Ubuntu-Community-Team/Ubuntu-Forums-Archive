---
title: "Failed to start the x server"
date: 2009-03-09
forum: General Help
---

### Post by Palms on 2009-03-09
Hi, 

I am a new Linux user (I installed xubuntu on my old computer yesterday).  My old computer is a 300MHz celeron with 256MB of ram and an S3 Trio64V2-DX/GX (775/785) display adapter.  It is an old machine (10 years old) but I was hoping to be able to try out some linux on it.  Windows 98 was originally installed on the machine, and the hard drive was partitioned during the Xubuntu installation.   

Ok, so the issues so far.  When I was installing Xubuntu, it said that it had to run in low graphics mode.  I installed Xubuntu and then after a bit of tweaking with the BIOS (I was getting a GRUB error 18 which is now fixed), I managed to get into Xubuntu.  First couple of times, it booted up fine.  Although, the resolution was horrible and I wanted to make it higher (to at least 800x600) but there was only one resolution offered to me in the setting->display menu.  (It would say that it was running in low graphics mode when I started up).  

So, I was trying to fix the resolution issue and ran the following instructions:

% sudo dpkg-reconfigure xorg

and then

% sudo dpkg-reconfigure -phigh xserver-xorg

I followed the prompts from the previous instructions, but to no effect.  However, now when I start up the computer, I get the message that it failed to start the x server.  After that, it goes to the terminal.  So I'm kinda stuck now as to how to get this working.  

If you need me to provide any extra information, just let me know.  Thanks in advance for helping.  

Regards,

Andrew

---

