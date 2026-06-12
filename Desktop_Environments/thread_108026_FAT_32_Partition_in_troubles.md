---
title: "FAT 32 Partition in troubles"
date: 2005-12-24
forum: Desktop Environments
---

### Post by Dearhell on 2005-12-24
I have a 120 GB HD, in 60 GB I had a NTFS partition with Windows XP, 30 GB with a FAT 32 partition (where I save my data like a security copy) and another 30 GB with Ubuntu

I wanted to reduce Windows partition and I delete the Windows XP partition and the Ubuntu one

After that I installed Ubuntu without any problem and the HD was like this: 

60 GB - Ubuntu, 30 GB - FAT 32 partition, 30 GB - Free

Then in the 30 free GB I tried to install Windows and all was well in the installation progress, but when the computer reboot it showed me a warning like this: "Incorrect Disk"

So I deleted the Windows and Ubuntu partitions and installed the Windows again, but the same warning appeared

At this moment I'm using Ubuntu Live, the FAT 32 partition works well (I have mounted it with this Live in order to test it)

Finally, what I want is to send the data from the FAT 32 partition to other computer of my local net.

I have internet in this Ubuntu Live machine and the computers of my net response to the ping, but I don't know how to configure Ubuntu to see them in the net in order to send the data from my FAT 32 partition, in Windows I hadn't to configure anything simply I clicked on net sites or type the IP in the explorer and I could going into them

So if anyone have a suggestion of what can I do . . .

Anticipate thanks

---

### Post by Dearhell on 2005-12-25
I think a way to restore the grub system will also work with this problem

I tried the option rescue of Ubuntu but it didn't work

How can I restore grub or delete it from the mbr in order to install right Ubuntu or Windows and get the data?

---

### Post by sciurus on 2005-12-25
If you have folders shared on your Windows machines, in your Ubuntu livecd session go to Places-'Connect to Server'. Select type as Windows Share. In the server field type the IP address of the Windows machine you want to connect to. In the User Name field type the name of your account on the Windows machine. Finally, type a name for the share in "name to use for this connection." Click connect and a folder with the name you just gave should appear on your desktop. Double click that folder and provide the password to your Windows account. You should then see the contents of the Windows share in Nautilus and be able to copy files to it if you have Windows set up to allow it.

---

### Post by Dearhell on 2005-12-25
Thx, I finally fixed the problem :D

---

