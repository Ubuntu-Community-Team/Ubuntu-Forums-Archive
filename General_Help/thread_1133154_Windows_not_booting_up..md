---
title: "Windows not booting up."
date: 2009-04-22
forum: General Help
---

### Post by Ansib on 2009-04-22
Hi, i've been looking around the forums for help and tutorials but haven't found a solution for 3 days now. So i've signed up to post my problem and see if anyone can fix it. I'm pretty much new to ubuntu and dont know anything about it really.

Anyway problem is i can't boot into xp. I turn on the computer and when it boots it just restarts in the middle of the process. I cant even access safe mode and i've even tried all the other options. I dont think its a hardware fault and might be virus related. I've tried using my XP CD but immediatly after i hit 'R' it just stays on the part where it says Examining (hdd space) at ide 0 on bus 0 (something like that) and it just doesn't budge. The same happens if i press enter to install windows. I've also tried Rescue CD but to no avail. Can anyone help? i'm running xp home edition.


Thanks.

---

### Post by 3Miro on 2009-04-22
Sounds like a dead HDD, which is no way an expert diagnosis.

You can download the Unubntu CD and burn it on a blank one (use a friend's computer). Then you should be able to boot from the CD (Try Ubuntu without changes to your system) and at least access some of your data with the hope of recovering it.

If the HDD is dead, there is nothing you can do short of getting a new one. The Ubuntu CD will at least let you save some of the data on your computer (how much depends on the deadness of the HDD, I once recovered everything and once could not recover a thing).

Try Ubuntu, you might like it.

---

### Post by Ansib on 2009-04-22
Thanks for the quick reply. I'm using ubuntu as i speak. Have been for 3 days. I don't think the HDD is dead. I can pretty much access it in ubuntu. I'll just wait until someone knows if they've been through this problem. Also i forgot to add that i get a BSOD just before the boot. Cant remember the string code though... 

Thanks for the help anyway :)

---

### Post by traderpats on 2009-04-22
Had an issue real close to this.  XP would start to start then would either reboot, bsod or shutdown.  I could still access my files via Ubuntu.  MY fix was to add the drive to a second computer. I then reformatted and ran a disk check with the utility set to mark any bad sectors.  The drive has been back in service now for months and no issues at all.  YMMV

PS This is a real good example of why, (in addition to daily backups), it's a good idea to format different partitions for OS, Programs and Storage...

---

### Post by Ansib on 2009-04-22
I'm really trying to sort this problem out without the need to format. Will it be ok if i brought a new ide hdd and installed that in ubuntu and formatted the damaged one? or i could install xp on the new hdd and then run some checkups on that drive. What do you guys think? i'll of course swap the hdds making the new one the primary and the current one a slave...

---

### Post by redspider on 2009-04-22
so you can't boot into either xp or ubuntu without a live cd? or can't boot into xp?

---

### Post by Ansib on 2009-04-22
I cant boot in windows. I'm running ubuntu off a live cd on the same machine at the moment

---

### Post by redspider on 2009-04-22
1 when booting up without the live cd does the grub menu show up? or 2 does it try to start xp automatically. if its number 1 check the grub menu with the live cd.  open terminal , "su" or "sudo" to root. "gedit". in gedit go open, then look for boot\grub\menu.lst .  open it. and check if it lists your boot options properly.

---

### Post by Ansib on 2009-04-23
hmm i actually haven't seen or used the grub menu, so i'm not very sure how i go about accessing it. And no this grub menu doesn't seem to show up if i boot without the live cd.

---

