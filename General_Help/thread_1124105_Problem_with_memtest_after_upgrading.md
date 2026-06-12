---
title: "Problem with memtest after upgrading"
date: 2009-04-13
forum: General Help
---

### Post by lloyd135 on 2009-04-13
Recently upgraded from Ubuntu 7 to the newest version. After I reboot, the computer goes into memtest. I read up about it and left it on all night.  Now that I've done that, it won't let me escape and reboot. I'm afraid of turning it straight off manually. In the corner it says "Locked" and I am unsure what it means by the keys CR etc...

I am using an Everex Cloudbook

Any help would be greatly appreciated.

---

### Post by antikristian on 2009-04-13
There's most likely something wrong with your grub config. Don't worry about restarting the computer while in memtest.

If you've got a bootdisk like for instance the ubuntu livecd, it can be remedied. by mounting the harddrive and manually editing the "default" value to something like "0"  in /boot/grub/menu.lst on the root partition of the harddrive.

---

