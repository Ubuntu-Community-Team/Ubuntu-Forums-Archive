---
title: "Cannot install grub"
date: 2010-01-20
forum: Desktop Environments
---

### Post by JimmieC on 2010-01-20
I have two hard drives, the first has Windows XP the second Ubuntu 9.1. Due to a backdoor trojan I had to delete my windows partition and then re-install XP , of course now I cannot boot Ubuntu. To fix this problem I installed a Live CD and then type "sudo grub" at a terminal but then get the message "grub not installed", and I cannot get beyond this message. I know this should work but for me it's not working. Any help please?

I have read the posts but they all use a live cd to fix the problem, what am I doing wrong?

Jim

---

### Post by whistlerspa on 2010-01-20
I can only say that I have exactly the same problem after a fresh windows install on hdd0. The live cd and terminal prompts just return error messages. 9.10.hdd1 has become inaccessible. I've also tried super auto grub but this stalls at the winbdows boot loader screen and will go no further.

I tried the suggestions of the following links but none of this worked either

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

and 

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by lev-unr on 2010-01-20
Did you try simply reinstalling Ubuntu?
 
I know that may sound like a pain in the butt, but I have found that for Grub issues that usually takes care of it. 
 
Also - I dont know if this applies to everyone, but whenever i am trying to Dual boot -i always make sure my windows is installed prior to installing ubuntu, I think windows likes to eat grub. : )

---

### Post by JimmieC on 2010-01-20
I haven't re-installed yet, I really, really, didn't want to do that but it looks like I may have to. I wish I didn't have to use Windows at all, this backdoor trojan thing not only has cost me a lot of time, but I don't know how much of my backed up data has been affected.

Jim

---

### Post by lev-unr on 2010-01-20
What ARE you using windows for?

---

### Post by JimmieC on 2010-01-20
I use Windows for video editing work, specifically I use Vegas Pro and some other editing software for editing HD video. I've heard of Linux Studio but haven't looked at it, but now I think I will!

What really ticks me off is that I use tons of antispyware, antivirus software, I don't download emails, I don't open attachments, and I don't do porn sites, but I managed to get infected with a bad trojan! I have about 100 passwords and now they have been compromised! No more, I'm no longer keeping passwords on Windows!

By the way, I re-installed Ubuntu 9.1 and that fixed my grub problem. Apparently one cannot use the "sudo grub" command with the 9.1 Live CD's like you can with the 9.04 Live CD's. Only problem is 9.04 Live uses an older version of grub which will not work with 9.1 Ubuntu.

Anyway, everything now works.

Cheers,

Jim

---

