---
title: "Delete file from windows drive"
date: 2006-04-03
forum: Desktop Environments
---

### Post by Zerocool10482 on 2006-04-03
Hi, I just wanted to delete a file from my windows external drive. Can anyone tell me how. I have virus on my friends PC and I want to delete it from Ubuntu.

Thanks. 

PS. I know he's now thinking about Ubuntu.

---

### Post by KingBahamut on 2006-04-03
Probably not,  If the Filesystem is NTFS its going to be hard. NTFS read/write access is purely experiemental and I advised strongly against it unless you know what your doing (or arent afraid to open a hex editor to rebuild the partition tables if you mess it up). If its Fat32, you should have no problem then mounting the partition (can even do it with a livecd) and deleteing the appropriate file.

---

### Post by Zerocool10482 on 2006-04-03
is ther a way I can scan with a anti-virus program then delete just some files?

---

### Post by KingBahamut on 2006-04-04
You MIGHT be able to use Clamscan/ClamAV to do it, but to remove the virus youll still need write persmissions against the drive, and if its NTFS, then your in the same bind.

---

### Post by Zerocool10482 on 2006-04-12
Thanks for the info. Is there a way though the command line.

---

### Post by Ramses de Norre on 2006-04-12
As said before: you just can't write on ntfs.
So no, there is no command tool that can do that.
In fact there is a way to write on ntfs but it's still experimental and it can ruin your partition tables which aren't that easy to recover.
So the best thing for you to do would be pulling out the hard drive, connect it to another windows computer and run a virus scan on the drive.

---

### Post by NoWhereMan on 2006-04-12
[QUOTE=Ramses de Norre]As said before: you just can't write on ntfs.
So no, there is no command tool that can do that.[/QUOTE]

I'm not sure, but maybe ntfstools (apt-get install ntfstools if i rememember) can (even without mounting the partition!).
Anyway, as Ramses said, it is very, very experimental. Once you do any change to the ntfs partition (still, if I remember) you should do a "ntfsfix /dev/ntfs_part_dev" to make winxp do a chkdsk on next reboot

---

### Post by Ramses de Norre on 2006-04-12
Isn't ntfstools the package that allows programs like gparted to resize/delete ntfs partitions? 
I think it is only possible to overwrite an existing file with it, and it has much restrictions and is very tricky..

---

### Post by NoWhereMan on 2006-04-12
[QUOTE=Ramses de Norre]Isn't ntfstools the package that allows programs like gparted to resize/delete ntfs partitions? 
I think it is only possible to overwrite an existing file with it, and it has much restrictions and is very tricky..[/QUOTE]

I'm not sure; i remembered you could do some basic operations... sure it is tricky...

---

### Post by Zerocool10482 on 2006-04-19
There's a howto in the forums. But thanks for the feedback.

Funny I can't find it but it didn't work.

---

