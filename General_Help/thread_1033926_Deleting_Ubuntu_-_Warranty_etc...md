---
title: "Deleting Ubuntu - Warranty etc.."
date: 2009-01-07
forum: General Help
---

### Post by Elycian on 2009-01-07
I'm sending in my computer because of some various reasons. When I was talking to the HP Tech guy he recommended deleting all personal information on the computer so I was thinking about just deleting windows and ubuntu altogether and installing windows fresh from the recovery disk anyways.

My question.
What would be the best method for deleting ubuntu and windows? Deleting the entire partitions with Gparted? A friend of mine told me deleting partitions wasn't very good for the hard drive though and usually ended up corrupting it. Now I'm not sure if he was trolling me.. but I just wanted to play it safe.
Also
does anyone know of a way you can get rid of GRUB and install the windows MBR without the windows disk? I was never given a disk for windows vista from HP and I don't want their tech guys to like freak out when they see GRUB. Despite the fact that they've probably already seen it before.

Thanks :D

---

### Post by oilchangeguy on 2009-01-07
> **Elycian said:**
> I'm sending in my computer because of some various reasons. When I was talking to the HP Tech guy he recommended deleting all personal information on the computer so I was thinking about just deleting windows and ubuntu altogether and installing windows fresh from the recovery disk anyways.

My question.
What would be the best method for deleting ubuntu and windows? Deleting the entire partitions with Gparted? A friend of mine told me deleting partitions wasn't very good for the hard drive though and usually ended up corrupting it. Now I'm not sure if he was trolling me.. but I just wanted to play it safe.
Also
does anyone know of a way you can get rid of GRUB and install the windows MBR without the windows disk? I was never given a disk for windows vista from HP and I don't want their tech guys to like freak out when they see GRUB. Despite the fact that they've probably already seen it before.

Thanks :D

boot from the live cd. go to the partition manager. highlight and delete the ubuntu partitions. and expand the windows partition to use the space. then reboot the computer, and there should be a prompt to press a key to enter the restore/recovery setup. then you can reload windows just like the day it came out of the box.

---

### Post by cariboo on 2009-01-07
If your hardware problem has nothing to do with the hard drive, you just zero out the hard drive and send it out for service, the service dept. can do a much better job of installing windows then you can.

To zero out the hard drive have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=516579").

---

