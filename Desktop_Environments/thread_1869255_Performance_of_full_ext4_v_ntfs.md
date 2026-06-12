---
title: "Performance of full ext4 v ntfs"
date: 2011-10-25
forum: Desktop Environments
---

### Post by Sekerob on 2011-10-25
Did not know how to phrase the searches so as to find an answer, so here goes:

Had a LiveCD with a -- persistent running from USB to find out if 11.10 had better performance, but it did not and just installed it over 11.04 after the upgrade caused more issues than it resolved. Originally installed the LTS 10.04 last year and it grabbed a piece of the Windows NTFS drive, which then got sliced in a 72GB ext3 system and a 3GB swap part. When going to 11.04 turned the fs into ext4. Now the question: when installing Ubuntu onto a ntfs partition, does one get the full ext3/ext4 floorwork or is there some emulation in-between? The issue is that if I run a science project (Clean Energy Project, phase 2 through BOINC distributed computing) under W7-64 on a quad I see a good 99% efficiency after a 8-12 hour run, but only 92-93 percent if booted into Linux. With efficiency I mean that the actual CPU is computing on the work and not distracted by disk IO e.g. (models up to 2GB). Both W7 and Linux run whilst there is no user input for the whole duration and when in Linux, even unload the GUI and per top, there's just parts of minutes a day on other tasks. When actually using the system, under W7 still getting a good 90-95% computing efficiency, but under Linux not getting even close to 80%, so wonder. Have played with swappiness, and fstab using parms such as noatime, relatime etc but it makes barely a difference. Even tried this zramswap-enabler script to stop the models flowing over into the on-disk VM i.e. purely run it from start/finish in ram except where the program does the mandatory progress saves to disk. From watching the System Manager graph, the VM is hardly used, often topping out at maybe 30-50MB.

What is it I'm overlooking not to get the same throughput as Windows.

TIA

--//--

P.S. Before I forget. The system has 4GB RAM, 3GB usable and a Q6600 CPU. The CEP2 program needs access to some 6700 static reference files i.e. they're only read, it's output written to 5 files that reaches maximum sizes of 30MB at most, together.

---

### Post by oldfred on 2011-10-25
Welcome to the forums.

Not sure what you are comparing. Why is only 3GB usuable. With 64bit or PAE on 32bit you should see all 4GB. But PAE is not fast.

Some comparisons, but wubi was faster on NTFS since it did some shortcuts that could be dangerous.

Speed comparison:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

### Post by Sekerob on 2011-10-25
Thanks for your reply. Your first link v.v the WUBI/LiveCD install into a NTFS drive, grabbing a piece and it not being a true full Linux drive is maybe the issue. Got a second drive on the shelf which I could plug in, so as to maintain the dual boot requirement. Would a new install modify the existing GRUB to point to that second drive when directing the installer to that second drive? My guess would be yes.

As for the memory, it's 64 bit Linux. Suspect it's the a hardware issue. W7 also refuses to acknowledge more than 3GB as usable, though like Linux is sees the full 4GB.

--//--

---

### Post by oldfred on 2011-10-25
If you use manual install to install to the second drive then you can choose which drive to install the grub2 boot loader into. Otherwise it defaults to sda.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Sekerob on 2011-10-25
Thanks for the pointer & links, oldfred. I'll figure it out tomorrow... today was the battle with fstab.

--//--

---

