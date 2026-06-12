---
title: "I cannot access ubuntu on dual boot machine"
date: 2009-04-28
forum: General Help
---

### Post by shateredsoul on 2009-04-28
HI,

I installed Ubuntu 9 recently, and decided to dual boot with windows xp media center edition.  Well I made a partition using the live cd and installed Windows xp.  Now I can't get back to ubuntu.. Windows automatically starts up whenever I restart or turn on my laptop.

Any ideas how I can install grub loader (I think that's what it's called)?  I mean, how can I change the settings so that when the system loads up I can choose between xp and ubuntu?

I would appreciate any help or pointers

---

### Post by shateredsoul on 2009-04-28
According to this link Windows Xp overwrote grub, any ideas on how I can reinstall it? I'm completely clueless

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1")

---

### Post by shateredsoul on 2009-04-28
question...

so i decided to reinstall ubuntu as a 2.5gig partition.. to get grub back.  It worked.  If i log in to my original partition w/ ubuntu and wipe that partition... will it also erase grub?  Or is grub on the swap partition?  

Someone ple3ase stop me if i'm about to kill my computer. please

---

### Post by stef4001 on 2009-04-28
Download super grub and repair your existing GRUB buth if you want to do dual boot with windows its better to install windows before linux wen you install linux hi wil find the boot.ini en put in the grub.
so in your case you can now reinstall ubuntu and the grub you wil recieve at bootup wil show your windows OS also.
wen you do repair grub you wil boot in to ubuntu but it wil not see your windows OS.
Have funn,

---

