---
title: "External Hard Drive Mount Error"
date: 2009-02-02
forum: General Help
---

### Post by viergeame on 2009-02-02
I recently got an external hard drive and when I plug it in I get several error messages.  I've had problems with external drives before, but not quite like this.  When I connect the drive I get two messages.

"Unable to mount OneTouch 4

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

"Cannot mount volume.

$LogFile indicates unclean shutdown (0, 0) Failed to mount 'dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the "Safely Remove Hardware" icon in the Windows taskbar then shutdown windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line:  mount -t ntfs-3g /dev/sdb1 /media/OneTouch 4 -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/OneTouch 4 ntfs-3g force 0 0"

I can't figure out where all the stuff about cleanly removing it is coming from.  I've never been able to get it to mount so I don't see how I could have unmounted it wrong.

---

### Post by Crafty Kisses on 2009-02-02
Have you tried rebooting your computer? That should solve that.

---

### Post by viergeame on 2009-02-02
Restarting, unfortunately, didn't fix anything.  I'm quite lost on what to do about this.

---

### Post by T3kG33k on 2009-02-02
I had a similar issue with a portable laptop SATA to USB HDD enclosure that I normally use with some Windows XP projects (fixing computers and Backing up data) but the drive was accidentally disconnected in a bad manor. I tried reconnecting the drive in windows and then properly disconnected the drive.  Went to the Ubuntu box and it then worked perfectly.

---

### Post by viergeame on 2009-02-02
I don't have windows on this computer, nor have I in ages.  The hard drive has never been used on a windows computer.  So should I just hook it up to a friends computer to do this?

---

### Post by T3kG33k on 2009-02-02
That's what I would try.  Since it appears that the drive was unmounted improperly on the computer.  What format is it in?  NTFS?

---

### Post by viergeame on 2009-02-02
Yes, it is ntfs.

---

### Post by T3kG33k on 2009-02-02
This is the easiest thing that I can think of right now.  If the drive is connected to a windows box (preferably XP) it will mount the device.  After that the drive should be properly disconnected.  Windows will finish leaving its dirty little mark on it stating that it's safe to connect to Ubuntu and it should work.

---

### Post by Neural oD on 2009-02-02
why don't u try forcing the mounting of the ntfs partition

---

### Post by Neural oD on 2009-02-02
btw  something like this should work:
sudo mount -t ntfs-3g /dev/device(put yours in here) /media/free_folder(you can create a folder in /media for mounting purposes - just make sure permissions are right) -o force

---

