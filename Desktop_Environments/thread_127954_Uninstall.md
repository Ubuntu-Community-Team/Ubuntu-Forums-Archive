---
title: "Uninstall"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Richa8 on 2006-02-10
How do I uninstall Ubuntu. I have a laptop that has both windows and Ubuntu and I want to retain windows.

---

### Post by Derek Djons on 2006-02-10
You don't uninstall an OS. There is no button with which you can command it to uninstall itself. But you can format the partition on which Ubuntu is installed. Windows itself has a limited Disk Management Utility build in. From there you can probably format the partition but you can't merge it with your current windows partition.

The best thing you could do is use applications such as Partition Magic which feature a rich disk utility set.

But after that your not done yet. Your MBR sector has probably been overwritten by Ubuntu's. But that I can't explain to you, never had to do it. So I hope someone else in the community can explain the rest for you.

---

### Post by sleipnir on 2006-02-10
To restore the Win Bootloader you have to boot from your Win CD and choose Recovery Console.

Then type the following commands

fixmbr c:
fixboot c:

Hope this helps

---

### Post by Derek Djons on 2006-02-10
Since I was planning to try out OpenSuSE Linux I formatted the Ubuntu parition on a spare computer's harddrive and used the fixmbr command (the machine is dual booted) and it works.

So if you're windows installation is installing by default selections and stuff, nothing should go wrong.

---

### Post by gmhafiz on 2006-02-18
[QUOTE=sleipnir]To restore the Win Bootloader you have to boot from your Win CD and choose Recovery Console.

Then type the following commands

fixmbr c:
fixboot c:

Hope this helps[/QUOTE]

My recovery cd from ASUS do not have that recovery console. Thus, I cannot use fixmbr. 

Currently, there is no windows in my hard drive. I only have ubuntu on root partition.

Even if i use the asus recovery cd and install windows, it still cannot boot into windows. Instead and Grub error 12 appears.

What can I do to in order to boot into windows? I tried deleting(formatting) all partitions but the grub is still in the Mbr.

---

