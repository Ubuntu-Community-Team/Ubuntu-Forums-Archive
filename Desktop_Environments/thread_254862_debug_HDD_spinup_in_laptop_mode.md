---
title: "debug HDD spinup in laptop_mode"
date: 2006-09-10
forum: Desktop Environments
---

### Post by jpb on 2006-09-10
I'm running Xubuntu 6.06.1 desktop, kernel 2.6.15-26-386 on an old Thinkpad 770 (Pentium-233, 96 MB DRAM, 5 GB HDD). Overall it works fine. I want to use it for a 24/7 data acquisition project where I want low power consumption and low noise, so I want the disk spun down as much as possible (with the lid closed, it uses 15 W with the somewhat noisy HDD running, and 10 W with HDD spun down). 

I configured laptop_mode for a spinup every 1 hour, but the drive actually comes on every 20 minutes or so, even with no user processes running, just the default system stuff. I tried to do the debug steps listed below from the forums archive to find out what's up, but only get this:

$ sudo echo 86400 > /proc/sys/vm/laptop_mode
bash: /proc/sys/vm/laptop_mode: Permission denied

How can I turn on the logging needed to find out what process is spinning up the disk?

------------
On June 8th, 2006 03:07 AM Ivan Matveich posted to ubuntuforums.org:    ...try this:

echo 86400 > /proc/sys/vm/laptop_mode
echo 0 > /proc/sys/vm/dirty_writeback_centisecs
echo 1 > /proc/sys/vm/block_dump
hdparm -y /dev/hda

When your disk spins up, run dmesg and you will see a line like:
[298735.484539] bash(11983): READ block 48497752 on hda1

which will tell you what process caused the unwanted read.

---

### Post by jpb on 2006-09-11
Solved it. I can write to the /proc system only as root, "sudo" isn't good enough. Since Ubuntu disables root by default, the process was:

1) enable root access with --> sudo passwd root
and set root password

2) become root with --> su

3) issue --> echo 1 > /proc/sys/vm/block_dump

works.

---

