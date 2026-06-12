---
title: "cd /dvd no eject"
date: 2005-07-20
forum: Desktop Environments
---

### Post by [pl]ice on 2005-07-20
hi, i have problems, very often upon umounting my cd's /dvd's; i can only re-boot the system, to my knowledge... i can't pin point the process to kill etc, 
   what is the solution for that? 
thanks!

---

### Post by frodon on 2005-07-20
If you want to force cd/dvd eject : ```
sudo eject cdrom0
```or cdrom1 it depends on wich cdrom you want to eject.

---

### Post by [pl]ice on 2005-07-20
yes, i tried this one, doesn't help, i got commands out like : device busy all the time, i  also tried umounting /dev/hdc (m y cdrom)  and umount /cdrom  -l does umount it (and other eg. /media/cdrom0), but i cannot then eject the media; mout says it has umount it.
 is there a way that i can find pid responsible for cdrom?

thanks

---

### Post by frodon on 2005-07-20
I had the same problem and when i type "eject cdrom0" it said that the device was busy but with "sudo" it works ... why it doesn't work for you ? ....  strange  :roll:

---

### Post by Takis on 2005-07-20
Do you have any terminal or other program that's in the directory you've mounted the cdrom? You need to leave the directory. Also, there is a bug in Konqueror where if you browse to a cdrom, and then browse somewhere else and try to umount the cdrom, umount says the cd's still busy. You need to close Konqueror to get past that.

---

### Post by [pl]ice on 2005-07-21
hm, i tried sudo , no sucess;
  yeh, i closed down terminals, and any other programs that i suspected using the cd-rom.

This would happen eg. using k3b, after recording, of kaffeinte, i can't really pinpoint it, or re-do the error myself; i havent checked dmesg, bit silly not to do so.

Could that be couse i haven't updated my kubuntu? i didn't bother because i have to re-partition everything..
thanks!
EDIT: after burning dvd, i can't mount it:
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

