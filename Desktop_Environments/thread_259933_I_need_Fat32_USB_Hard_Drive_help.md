---
title: "I need Fat32 USB Hard Drive help"
date: 2006-09-18
forum: Desktop Environments
---

### Post by SirShaggy on 2006-09-18
Hi All,
I have 2 usb hard drives. Both are Fat32 and have 2 equal partitions. I would like to include these into my /etc/fstab to automount at boot. Problem is, I can't make sense of what all I've read on the forums and web. Stuff like "noauto" "FID=", "GID=", "defaults" etc....
Here is what I know:
I made a directory, /media/sda1, /media/sda2, /media/sdb1, /media/sdb2.
That directory is where I'd like them to mount as they have media on them and then I can remember where they are.:wink: 
All partitions are Fat32 and the owner and group is me, "shaggy".
I want read and write permissions to use these drives on Ubuntu, Fedora and Windows XP:roll:  at work.

Here is my current fstab, in case....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               reiserfs defaults        0       1
/dev/hda1       /boot           reiserfs notail          0       2
/dev/hda5       /home           reiserfs defaults        0       2
/dev/hda9       /media          reiserfs defaults        0       2
/dev/hda6       /usr            reiserfs defaults        0       2
/dev/hda7       /var            reiserfs defaults        0       2
/dev/hda2       none            swap    sw              0       0

Can anyone guide me as to what to write into my fstab to make both drives/all 4 partitions automount at boot? Thanks for your time,
SirShaggy

---

### Post by orb9220 on 2006-09-18
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

Hope it helps

---

### Post by SirShaggy on 2006-09-18
Umm, no. Unfortunately that appears to be far above me! Actually, I followed it for a bit, then when it came time for the rules, he added options to his and I don't understand how to come up with them and from where?!?!](*,) 

I am just too new at this still. I can do some things now that I couldn't before, this just seems utterly impossible for me to understand. I'm sorry about that.:frown: 

Is that the only way? I guess I can just try to make something up and hope it works. I just really don't understand.

---

