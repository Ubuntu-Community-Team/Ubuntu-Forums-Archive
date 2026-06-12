---
title: "NTFS Drives"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Muntted on 2006-09-18
I am just starting with Ubuntu. After a day of work I have successfully setup my 2 monitors, used easyubuntu to setup my nvida drivers, downloaded a few games etc.

However, it seems when I go to Places > computer, if I click on my NTFS drives they wont open. That is untill I go into /media and open them up from there. After that I can access the drives via computer.

Is this normal? Do I fix this by mounting? Last time I tried mounting, they disappeared from computer.

Cheers

---

### Post by madmetal on 2006-09-18
ntfs access is not fully supported by linux(and ubuntu) and is not recommended..
if you have media or other files you want to access from both linux and windows the best way is to create a fat32 partition and place your files there..

---

### Post by Muntted on 2006-09-18
Well thats a bit impractical since I also run windows and have all my windows drives as NTFS.

---

### Post by edm1 on 2006-09-18
I know...windows is impractical in that it doesn't use the ext3 filesystem isn't it?

---

### Post by Muntted on 2006-09-18
completely lol. Im nowhere near ready to release control of my pc completely to ubuntu, so I was just wondering if there was a way around this problem.

---

### Post by konst88 on 2006-09-18
convert the NTFS to FAT32 using partition magic.

---

### Post by edm1 on 2006-09-18
Ubuntu to able to read the NTFS filesystem and to an extend write it but this is still experimental. If you would like both Windows and Ubuntu to be able to read+write i'd recommend creating a new FAT32 partition (this is what i did before i got rid of windows). There is a guide [here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") that will help you add your windows drives to fstab so that they're mounted at startup.

---

### Post by Muntted on 2006-09-18
all I pretty much want to do is read at the moment, ill try that guide. Thanks

---

