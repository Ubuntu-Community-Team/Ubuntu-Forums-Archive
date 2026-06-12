---
title: "Bypass GRUB select menu"
date: 2011-06-30
forum: Desktop Environments
---

### Post by ben44b on 2011-06-30
Hello,

Seems like a simple step but I can't seem to find the answer. I have Wubi installed with Windows 7 and Ubuntu 11.04 installed. 

When I start-up the computer, I get the Wubi menu. That's fine. It defaults to Ubuntu. 
I just want to bypass the following GRUB menu and have it automatically select the first item in that menu without having to hit ENTER all the time. 

Thanks.

---

### Post by bcbc on 2011-06-30
This is being fixed for the next release (11.10) but currently there is no (easy) way to hide the grub menu when grub detects more than one OS on the system.

You could try [this]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:") - but it was written a while ago so you might need to check it against the current version of grub2.

PS if you want ubuntu to be the default it might be a good time to consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") or reinstalling direct to partition. Wubi is great to try Ubuntu out but for long term use it's better to partition and install direct.
If you stick with Wubi, avoid hard poweroffs (if Ubuntu is hanging try Alt+SysRq R-E-I-S-U-B instead) and also consider keeping important data backed up off the virtual disk.

---

