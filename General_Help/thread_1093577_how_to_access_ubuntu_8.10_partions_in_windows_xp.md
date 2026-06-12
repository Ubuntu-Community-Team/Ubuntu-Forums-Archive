---
title: "how to access ubuntu 8.10 partions in windows xp"
date: 2009-03-11
forum: General Help
---

### Post by garifo on 2009-03-11
Is there a way I could access the ubuntu 8.10 partitions in windows xp?
I have installed the following tools in windows XP Linux Reader, expres2fs, and DiskInternals.  I do see the linux partitions but when I attempt to open them I always get the partition needs formatting.  Anyone else done this before?

Or Maybe someone can point me in the right direction with what I'm trying to accomplish.

I have a box with windows xp and ubuntu 8.10 where sometimes I need to remote into windows xp and other times into ubuntu 8.10.  My main boot is Ubuntu 8.10.  When I remote into ubuntu I am able to change the boot order by then making windows the primary boot.  I reboot and now i'm able to remote into windows.  But if now I want to go back to Ubuntu.  I see no way of changing the primary boot back to Ubuntu.  Both OS are in the same HD.

Thank you in advance for your help.

garifo

---

### Post by kanikilu on 2009-03-11
Sorry this doesn't answer your question, but I tried to use a similar tool on XP (can't recall the name now) and got nowhere...

---

### Post by garifo on 2009-03-12
anyone else?
is it possible to move the menu.lst to a fat32 partition where both windows and ubuntu 8.10 will have access too?
if so anyone can point me to the right steps?

---

### Post by 73ckn797 on 2009-03-12
Look for "Ext2IFS_1_11a.exe" to read "ext2" format from Windows.

Find it here: [http://www.fs-driver.org/](http://www.fs-driver.org/) 

Also look for "Super Grub Disk". Here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

 Burn the iso to CD and reboot computer from that. It can do all sorts of grub configuring for you.

---

### Post by garifo on 2009-03-12
I tried Ext2IFS_1_11a.exe and it did not work.  I see the HD but when I try to access it I get a message asking me if I want to format the drive.
I will try the other suggestion.

thanks
> **73ckn797 said:**
> Look for "Ext2IFS_1_11a.exe" to read "ext2" format from Windows.

Find it here: [http://www.fs-driver.org/](http://www.fs-driver.org/) 

Also look for "Super Grub Disk". Here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

 Burn the iso to CD and reboot computer from that. It can do all sorts of grub configuring for you.

---

### Post by 73ckn797 on 2009-03-12
> **garifo said:**
> I tried Ext2IFS_1_11a.exe and it did not work.  I see the HD but when I try to access it I get a message asking me if I want to format the drive.
I will try the other suggestion.

thanks

Is the Ubuntu file system ext3? I cannot read ext3 but can read ext2.

I have not pursued the issue any further since I only need to access Ubuntu from Windows on my laptop and it is the ext2 format which the reader I linked you to works fine on it. I have 3 drives in my desktop computer with Ubuntu 32 on one and 64 on the other. One is the ext2 format and can be read from Windows.

---

### Post by garifo on 2009-03-12
Sorry...yes I forgot to mention it's ext3 and not ext2.

So say since the tools only read ext2, can I change from ext3 to ext2 with my current linux partition?
If yes any easy way of doing it?

thank you

---

### Post by theozzlives on 2009-03-12
> **garifo said:**
> Sorry...yes I forgot to mention it's ext3 and not ext2.

So say since the tools only read ext2, can I change from ext3 to ext2 with my current linux partition?
If yes any easy way of doing it?

thank you

That's not true I used  the fs drivers  when I had dual boot and didn't have  a  problem. The only dif. btw 2 and 3  is the  journaling. the fs driver should work.  The onee I  used was  ext2ifs.

---

### Post by garifo on 2009-03-12
Not sure why I keep getting the message though...see attached screen shot.

---

### Post by 73ckn797 on 2009-03-12
> **theozzlives said:**
> That's not true I used  the fs drivers  when I had dual boot and didn't have  a  problem. The only dif. btw 2 and 3  is the  journaling. the fs driver should work.  The onee I  used was  ext2ifs.

Did you simply install the reader and it worked with ext3? I have had no success reading ext3 and get the same error "garifo" posted. Is there any config info that can be modified?

---

### Post by garifo on 2009-03-13
> **theozzlives said:**
> That's not true I used  the fs drivers  when I had dual boot and didn't have  a  problem. The only dif. btw 2 and 3  is the  journaling. the fs driver should work.  The onee I  used was  ext2ifs.

What version of the software were you running? also were you on ubuntu 8.10?

---

### Post by 73ckn797 on 2009-03-13
> **garifo said:**
> Sorry...yes I forgot to mention it's ext3 and not ext2.

So say since the tools only read ext2, can I change from ext3 to ext2 with my current linux partition?
If yes any easy way of doing it?

thank you

To change from ext2 to ext3 would require reformatting the partition which would destroy any data. I know of nothing else to accomplish what you ask. You would have to back-up important data and re-install, formatting to ext2.

---

### Post by garifo on 2009-03-13
> **73ckn797 said:**
> To change from ext2 to ext3 would require reformatting the partition which would destroy any data. I know of nothing else to accomplish what you ask. You would have to back-up important data and re-install, formatting to ext2.

Thanks...i guess i will give that a try it out on VMware first.

---

### Post by gladson1976 on 2009-03-27
hi all

i've been having the same problem and i've found a driver that works with ext3 with 256 byte inodes.

try the Ext2Fsd driver at
[http://ext2fsd.sourceforge.net](http://ext2fsd.sourceforge.net)
it works with both read and write support.

---

