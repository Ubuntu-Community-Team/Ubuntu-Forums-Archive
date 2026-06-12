---
title: "Error 13"
date: 2009-04-08
forum: General Help
---

### Post by snkngshps on 2009-04-08
I've posted this in the development section (I'm running Jaunty) but so far I haven't been able to get a response and my computer is currently inoperable. It seems like a problem that can be resolved regardless of version number.


I just ran some updates with Jaunty and it prompted me to restart. I accepted and now I can't boot the computer! This is the error I'm getting:

Code:

Boot from (hd0,0) ext4 6ef3621e-9e0e-4b8c-8d58-ef61a508becf

Error 13: Invalid or unsupported executable format

Press any key to continue...

I googled this error and it seems to be happening with people that are dual booting XP and Ubuntu and mess up their grub loader, but I'm only single booting Ubuntu and haven't messed with the grub loader at all. Any ideas?

---

### Post by ryanhaigh on 2009-04-08
Just a guess but are you sure that grub can handle ext4 volumes?

---

### Post by Nebutron on 2009-04-08
[/QUOTE] I just ran some updates with Jaunty and it prompted me to restart. I accepted and now I can't boot the computer! This is the error I'm getting:


I googled this error and it seems to be happening with people that are dual booting XP and Ubuntu and mess up their grub loader, but I'm only single booting Ubuntu and haven't messed with the grub loader at all. Any ideas?[/QUOTE]

Sounds like a probably grub issue.  I have run into the same kind of error when installing Hardy and Intrepid on a HD that had a previous linux distribution and was reformatted. Seems reformatting left some remnants on the MBR that caused problems. When I wiped the drive using Parted Magic, it resolved the issue for me.  Another thought would be to run Supergrub, but I have only had limited success with that.  :cool:

---

### Post by drs305 on 2009-04-08
Yes I had the same problem the other day. My system has ext3 intrepid and ext4 (converted after install) jaunty. It broke on an update. I later read that in such cases (before the crash) you should run update-grub (now they tell me).

Anyway, the fix for me was to accomplish the following from the livecd:
[http://ubuntuforums.org/showthread.php?t=1104822&highlight=ext4#5]("http://ubuntuforums.org/showthread.php?t=1104822&highlight=ext4#5")

Check TBD's post 5.

---

### Post by snkngshps on 2009-04-08
> **drs305 said:**
> Yes I had the same problem the other day. My system has ext3 intrepid and ext4 (converted after install) jaunty. It broke on an update. I later read that in such cases (before the crash) you should run update-grub (now they tell me).

Anyway, the fix for me was to accomplish the following from the livecd:
[http://ubuntuforums.org/showthread.php?t=1104822&highlight=ext4#5]("http://ubuntuforums.org/showthread.php?t=1104822&highlight=ext4#5")

Check TBD's post 5.

Thank you!! After doing much more extensive searching that does seem to be the problem. I thought I had destroyed my hard drive so I'm glad that's not the cause. I'm burning a Jaunty live-cd now so I can get in there and poke around. I had updated to ext4 with no problems and many restarts without any issues. But some random update today, I don't even know what it was, broke it somehow.

---

