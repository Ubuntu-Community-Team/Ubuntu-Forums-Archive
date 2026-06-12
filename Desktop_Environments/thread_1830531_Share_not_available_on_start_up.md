---
title: "Share not available on start up"
date: 2011-08-21
forum: Desktop Environments
---

### Post by koala15 on 2011-08-21
Summary of issue: When 11.04 (Natty) with Unity starts, a share on a (second) non-system disk is not available until I view the disk though the "File System" GUI.

Environment:


[LIST]
[*]OS: 11.04 (Natty) with a working Samba environment, clean install (not an upgrade)
[*]Desktop: Unity
[*]Updates: All updates applied
[*]Disks: 2 physical disks (2 x 1tb WD),
[*]Natty installed on 1st disk (formatted "Ext4")
[*]non-system data on 2nd disk (formatted "Ext4")
[*]One partition on each disk (spanning entire disk,
[*]System disk partition type is 0x83 (Linux),
[*]Data disk partition type is 0x07 (NTFS).
[*]_***Share: Applied to root of 2nd disk.***_
[/LIST]

Problem details:

[LIST=1]
[*]Share and disks work faultlessly, access to the share from Win7 works.
[*]Data disk icon is displayed (automatically) on desktop and in Unity task bar
[*]After reboot:
[/LIST]

[LIST]
[*]Data disk icon does not show on desktop or in task bar
[*]Data disk (share) not accessible from Win7
[*]After accessing File System GUI and navigating to data disk, the data disk automatically shows up on desktop and task bar.
[*]Also once I access the data disk from the file system GUI, the share (from Win7) suddenly works
[*]When I say "access the data disk", all I have to do is **view **the contents, no changes
[/LIST]
Help please as I need to locate the machine remotely and reboot it remotely and not necessarily login to use the GUI.

Thank you all.
BTW 11.04 is GREAT :)

---

### Post by koala15 on 2011-08-21
SOLVED IT!!!!

20 minutes after posting the initial message, while making a cup of coffee I solved it ...... 

The problem is that "automount" only mounts the 2nd disk when it is accessed, BUT it seems that trying to access the disk from a remote win7 (or any other system) does not activate the "automount".

Solution: I installed "pysdm" and instructed it to mount the disk at boot time. NOW IT WORKS!!!!! BTW: for those who do not know: "pysdm" is a GUI method to edit "fstab".

If you wish to see a brief description of "pysdm" [please see here]("http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html"). For a much more detailed explanation of "pysdm" [please see here]("http://ubuntuforums.org/showthread.php?t=872197").            :popcorn:

---

