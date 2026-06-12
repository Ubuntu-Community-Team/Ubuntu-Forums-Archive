---
title: "Sharing Files on Partition with Windows XP and Ubuntu"
date: 2006-01-09
forum: General Help
---

### Post by boarhog on 2006-01-09
Hello All, I have been using Ubuntu for about 5 months and absolutely love it. I have been converting the neighbors. 

Anyway, here is my question, I have a small home network with 4 computers, 2 XP, 1 XP/Ubuntu dual boot, and one exclusively Ubuntu Linux. I have the Ubuntu system paritition with and EXT2 and a VFAT/FAT32 partition for file sharing. 

The ubuntu system can see the Windows PC's fine and retrieve files off the VFAT partitions I have set up on the Win systems for file sharing between Windows and Linux. 

The WinXP machines can see the Ubuntu PC with no issues as well. The problem lies when I try to access the Ubuntu machine from WinXP. It asks for a User ID and Password. 

On My Windows machines there are no passwords and when I try the Ubuntu user ID and password it will not accept it. It also will not allow me to leave it blank either. Printer sharing works fine, this is the first time I have tried to share files from a WinXP machine to a Linux machine.

Thanks for any guidance.

Scott

---

### Post by tappad on 2006-01-09
I belive that you set up users and passwords in smb.conf

Dont know if ive been any help at all..

Regards.
David

---

### Post by KermitJr on 2006-01-09
smbuseradd
smbpasswd

---

### Post by TrD on 2006-01-10
I have the same problem, both my ubuntu machine and XP machine ask for user names and passwords and in the ubuntu machine the default account doesnt work. the xp machine doesnt have any password.

---

### Post by sabredog on 2006-01-10
I tried a few online faq's to assist me as well and still no joy. Be handy to know.

---

### Post by boarhog on 2006-01-21
I still have no luck, I guess I will have to wait until the next version of Ubuntu comes out. Maybe this will be easier in the next version. I would really like Linux to be able to give XP and MAC a run for the money for the desktop. It is not quite there but getting there. Thanks for the help.

Scott

---

