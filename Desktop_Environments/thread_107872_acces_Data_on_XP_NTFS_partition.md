---
title: "acces Data on XP NTFS partition"
date: 2005-12-24
forum: Desktop Environments
---

### Post by Hawkeye8081 on 2005-12-24
Is it possible to acces my data on an winxp NTFS partition with ubuntu?

I have a sata raid drive.

---

### Post by xmastree on 2005-12-24
This:
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
explains how it's done.

Remember, linux can't write to NTFS, so it will be read-only.

---

### Post by gsdefender on 2005-12-24
You should otherwise use Captive, but it is not at all recommended.

---

### Post by NewbieNik on 2005-12-24
Yes, but you will need Samba and permission to the XP drive.

Use:-

sudo apt-get install samba

On the terminal. 
Then you should have access to windows partitions on the same box.
Windows networking is more compicated, but visit [http://www.samba.org](http://www.samba.org) for some great documentation....

---

### Post by NewbieNik on 2005-12-24
[QUOTE=xmastree]This:
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
explains how it's done.

Remember, linux can't write to NTFS, so it will be read-only.[/QUOTE]

Really??? I seem to be writing to NTFS partitions on my windows 2003 server without issue.

---

### Post by adie273 on 2005-12-24
keep in mind, when going by the instructions on the URL xmastree gave you...

with it being sata you may need to replace the '/dev/hda' etc, to '/dev/sda'

Adie

---

### Post by kosmic on 2005-12-24
Linux can write to NTFS partitions with the Captive drive, but don't forget to always umount the drive first if you reboot your box :)

---

### Post by xmastree on 2005-12-24
[QUOTE=NewbieNik]Really??? I seem to be writing to NTFS partitions on my windows 2003 server without issue.[/QUOTE]
I'm talking about linux writing to an NTFS partition in the same computer. I think you mean linux is sending data over a network to a Windows 2003 computer, which then writes it to its NTFS disk. So linux isn't actually **writing** to the NTFS disk

---

### Post by NewbieNik on 2005-12-24
My apologies xmastree... Haven't really given much time to my dual-boot system. Love running Ubuntu on its own system.

---

