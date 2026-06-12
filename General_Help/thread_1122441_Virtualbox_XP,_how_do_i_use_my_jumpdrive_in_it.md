---
title: "Virtualbox XP, how do i use my jumpdrive in it?"
date: 2009-04-11
forum: General Help
---

### Post by tabarnackle on 2009-04-11
hey i have xp installed on a virtual machine in virtualbox, and i have a jumpdrive that needs to be formatted on xp, (u3 crap, i wont go into detail)
the problem im having is when im on xp and plug in the jumpdrive, it mounts in ubuntu.

---

### Post by dcstar on 2009-04-11
> **tabarnackle said:**
> hey i have xp installed on a virtual machine in virtualbox, and i have a jumpdrive that needs to be formatted on xp, (u3 crap, i wont go into detail)
the problem im having is when im on xp and plug in the jumpdrive, it mounts in ubuntu.

Go to the Virtualization forum and read the FAQ, it has plenty of info on using VM USB devices.

---

### Post by callie510 on 2009-04-11
Yeah, read the FAQs, but I'd like to just make a comment here. I had so many headaches with VirtualBox and USB before I figured one simple thing out. Make sure you are *not* using VirtualBox OSE as that doesn't support USB - only the VirtualBox version (still free, but not OSE) does.

If you're using the right version of VirtualBox.... as long as you unmount the drive in Ubuntu, VirtualBox should then get access to it. You can give VirtualBox's Windows access to it through Devices. You can also right click the little USB icon in the bottom tray. This is how I sync my iPod with iTunes in Virtualbox.

---

### Post by tabarnackle on 2009-04-11
how do i give it windows access through devices? i tried unmounting it and thats not working thanks

---

