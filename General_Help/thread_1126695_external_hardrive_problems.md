---
title: "external hardrive problems"
date: 2009-04-15
forum: General Help
---

### Post by numbness05 on 2009-04-15
Hey there I'm having huge difficulties with trying to mount my external hard drive after trying to copy some video files to it this morning....
It paused half way through me transferring and removed it self from my desktop ever since I have not been able to remount it and have been given two boxes stating the following:-

Unable to mount Danny
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Unable to mount the volume=
$MFTMirr does not match $MFT (record 0). failed to mount'/dev/sdf1';input/output error NTFS is either inconsistent or you have hardware faults, or you have a softRAID/FakeRAID hardware. In first case run chkdsk /f on windows then reboot into windows TWICE.. The usage of the parameter is very important ! If you have SoftRAID/Fake RAID then firstypu must activate it aand mount a different device underthe /dev/mapper/directory, (e.g. /dev/mapper/nvidia_eahaabcc1)
Please see the 'dmraid' documentation for the details 

I really have no idea what any of this means... does any body have any idea what could be causing this problems and how I can easily rectify it please...every thing I own is on there and really need to gain access to it all quite urgently..

many thanks in advance

---

### Post by fjgaude on 2009-04-16
Please, more details as to what the "external drive" is? Were you deleting source files as you copied to the external?

---

### Post by Psychopump on 2009-04-16
I had this issue a while back.

I don´t know why, but this helped:

-Boot into an XP machine.
-Plug in the external drive
-Use the "safely remove hardware" app in the taskbar
-Stop the external HD with the app
-Remove the HD
-Boot into Ubuntu...problem fixed!

---

### Post by iiiears on 2009-04-16
It seems possible that the disk was unplugged before writing all the journaling info to disk. 

More information here.
CHKDSK
[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265) 

~Best Wishes

---

