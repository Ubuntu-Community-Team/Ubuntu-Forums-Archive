---
title: "My mp3 player won't mount..."
date: 2009-03-05
forum: General Help
---

### Post by lemonbar on 2009-03-05
It did at first, but I messed up some stuff.  Apparently my mount point syntax is wrong, and now that I can't get it to mount at all, I can't change the settings in the properties window.  How do I fix it?
 Here's the history (from another thread)
>  MP3 player - read only?
I have a new 8gb Memorex mp3 player - I had it working okay (using Intrepid on my pc, btw), but last time I tried to add and remove songs, my computer crashed and I lost everything on the player - even the browser. I reset the player, and it's functional (radio works, mic works, I can change the skins, yada yada), and once the computer was running again, I tried to put music on the player (which is empty aside from the basics). I get an error message now that says "read only" permission. I opened the properties window to change the permissions to "read and write," restarted, and still receive the same error message. I've looked all over for the answer but am overwhelmed by all the advice - does anyone have...

The Answer?

I'm about to go crazy.

[Here's the thread]("http://ubuntuforums.org/showthread.php?t=1085858") so you can see where I screwed up.  There's so much I don't know about computers. Thanks in advance for all support and replies - I know this is all out of the goodness of all your hearts, and your help is much appreciated.<3

---

### Post by mb_webguy on 2009-03-05
Changing the permissions in the properties dialog will only change those properties for the current mount, and won't affect the next time the device is mounted -- such as when you reboot the computer.

I don't know why exactly your mp3 player isn't mounting correctly, but here's one thing you can try.  Open the terminal and run the command "sudo apt-get install pmount".  Plug in the mp3 player.  In the terminal, type "sudo fdisk -l" (and that's a lowercase "L", btw, and not the numeral "1").  Find the entry for the mp3 player, and note the device being used -- it's the bit that goes something like "/dev/xxxn".  

Now use the command "mount | grep /dev/*xxxn*" (where xxxn is the device found with the previous command) to see if the mp3 player is mounted (which is probably in the /media directory).  If it is, note where it's mounted, and type the command "sudo umount /path/to/mountpoint" to unmount it.

Now to mount it with read/write permissions, type "pmount /dev/xxxn".  Make sure you unmount it when you get done, either in the file manager or using the command "pumount /dev/*xxxn*".

---

### Post by lemonbar on 2009-03-05
Just so I don't really mess it up, I'm going step by step.  I installed pmount and ran this:
> mount | grep /dev/sdb1
and got this:
 > 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33b7e551                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9495    76268556   83  Linux 
/dev/sda2            9496        9729     1879605    5  Extended
/dev/sda5            9496        9729     1879573+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 7933 MB, 7933526016 bytes
256 heads, 52 sectors/track, 291 cylinders
Units = cylinders of 13312 * 2048 = 27262976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         291     7747480    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 52) logical=(0, 1, 1)


Then I did this:

> mount | grep /dev/sdb1

and nothing happened - I just got the command line.  Also, when I plugged in the player, I got a dialog box that said "> **Unable to mount 7.9 GB Media**
DBus error org.freedesktop.DBus Error.  NoReply: Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

and another one which said:

> **Cannot mount volume.**
Unable to mount volume.
Details
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually/)

What does it all mean?  

It means I shouldn't mess with the workings of my computer when I'm tired from work, that's what it means:)

---

### Post by lemonbar on 2009-03-05
I think the problem is somewhere in here:

> Device Boot Start End Blocks Id System
/dev/sdb1 * 1 291 7747480 b W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(0, 0, 52) logical=(0, 1, 1) 

---

### Post by lemonbar on 2009-03-06
So, how would I get in there and edit it?  I looked up the fstab tutorial, and I'm still a little unsure how to proceed.  I've been guessing wrong pretty consistently, and still I have a device I can't use.

> Disk /dev/sdb: 7933 MB, 7933526016 bytes
256 heads, 52 sectors/track, 291 cylinders
Units = cylinders of 13312 * 2048 = 27262976 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 291 7747480 b W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(0, 0, 52) logical=(0, 1, 1) 

It mounted when I plugged it in the first time, so I know it's possible to get it working.  The player is still functional, and I can listen to and record the radio, but I'd love to be able to fill up all the rest of the gigabytes.

---

