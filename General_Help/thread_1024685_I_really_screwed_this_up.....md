---
title: "I really screwed this up...."
date: 2008-12-29
forum: General Help
---

### Post by Anonymous111 on 2008-12-29
I used to dual boot ubuntu and windows xp on my other comp...now i don't boot.  For some reason Ubuntu 8.04 got really screwed up....i couldn't even boot with the CD i used to install it.  So, sadly, i had to take the ubuntu partition off my hard drive.  I repartitioned my hard drive and now im getting a grub error when i try to turn on my computer...

I don't really want an answer telling me how to get Ubuntu to work again, as i have it installed on this comp and its working perfectly, just how to get xp to boot on my other comp...  
(I dont have the XP install disc)

---

### Post by kokkus on 2008-12-29
You really didn't have to delete the ubuntu partition.
Before grub comes up, isn't there a message that says something about click F2 (or something) to go to setup?
When you are in the setup menu, choose to boot from your CD room and not the hard driver. You can choose CD Rom as first boot and harddriver as 2nd. Now reboot with the cdrom in your computer and install your ubuntu or windows or whatever you wish.
Now when you have an operating system you can choose to boot from your hard driver again and install your second operating system.

---

### Post by wesley_of_course on 2008-12-29
I've ran across the same challenge  and Super Grub was a blessing .
It just works , keep a copy on hand for just those moments when it's needed , ( out and about ) , need to boot from the  cd but thats  no problem . 

                    [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Good Luck

---

### Post by Anonymous111 on 2008-12-29
I think you both misunderstood my question.  My computer will not boot ANY OS.  I choose to boot from the hard drive and then it says:
"
GRUB loading, stage1.5.

GRUB loading, please wait...
Error 22
"

To clarify, I have ubuntu on the computer im typing this from atm.  I do not need it on the one thats screwed up.  I just want to get it so it will let me boot into windows.  I do NOT have the windows install discs, xp was pre-installed on the computer.

---

### Post by wesley_of_course on 2008-12-29
That's the beauty of Super Grub - it's not an OS ; it will " restore your boot " ,.

---

### Post by Anonymous111 on 2008-12-29
Well, Super Grub sort of worked....but it only detected the Windows recovery partition, not the one im trying to boot, I just gave up on this and reformatted the Windows partition, then restored it to its original condition...

---

### Post by jiangshi on 2008-12-29
There are a couple of ways to approach this - 

1) Boot to a Linux install CD. You might need a distro other than Ubuntu. I am new to Ubuntu, so I don't know how flexible or easy it is to use for fixing Grub problems. The SuSE install boot disk, for example, gives you an option of repairing the boot sector. Boot to the install CD and start an install, after a screen or two, you will have an option as to what type of install you want. Choose Other... This gets you to some repair options. You want to repair the booting. You can then point Grub to your Windows partition if it is still intact. You can download SuSE CD 1 iso image from Novell. You will only need CD 1 for this option or the one that follows. If you cannot do this easily, then -
 
2) You might try reinstalling Linux, and manually configure the installation for dual booting. Use a minimal Linux installation, since you are not really wanting to use Linux on the machine. You can resize the Linux partition to almost nothing. The end result is that you will have a viable Grub menu to get to your Windows partition if it is still recognisable by Linux. If it is not, then the whole Windows partition is trashed. In which case, do the following paragraphs, but you will need to borrow someone's Windows installation CD. I suggest a version of Windows that does not need to be activated over the Internet. Windows 2000 is a good version of Windows and does pretty much everything that XP does and it does not have to be activated or registered, and it is still supported by Micro$oft.

Here's the problem. This situation occurs when setting up a Windows machine for dual booting to Linux. Part of Grub gets installed in physical disk sectors 0 and 1 on track 0 side 0. Even if you had your Windows install CD, the Windows install does not clear out or over-write all of the Grub stuff. So when you start your computer, you get the error that you are getting. At least this is true for Windows versions older than Vista. I don't know about Vista. I've never used or installed it.

Here's the fix - I've run into this problem a hundred times, and every time I have to use a disk editor, like Norton's DiskEdit, to zero-out those two sectors mentioned above.  Then I can successfully install Windows. If you do not have a disk editor program that can write to absolute sectors in hex (binary) on your hard drive, then go to [www.tucows.com](www.tucows.com) and search for a disk editor. I know they are around for free. HOWEVER, since you have no Windows install CD's, this is not an option for you. I write it here for information only, or in case your Windows partition is trashed.

Somebody else may have a more elegant solution to this problem, and if they do, maybe they will be kind enough to post it.

---

### Post by jiangshi on 2008-12-29
There are most likely several ways to approach this. Here are two that I know about and have used - 

1) Boot to a Linux install CD. You might need a distro other than Ubuntu. I am new to Ubuntu, so I don't know how flexible or easy it is to use for fixing Grub problems. The SuSE install boot disk, for example, gives you an option of repairing the boot sector. Boot to the install CD and start an install, after a screen or two, you will have an option as to what type of install you want. Choose Other... This gets you to some repair options. You want to reinstall the Grub boot loader. You can then point Grub to your Windows partition if it is still intact. You can download SuSE CD 1 iso image from Novell. You will only need CD 1 for this option or the one that follows. If you cannot do this easily, then -
 
2) You might try reinstalling Linux, and manually configure the installation for dual booting. Use a minimal Linux installation, since you are not really wanting to use Linux on the machine. You can resize the Linux partition to almost nothing. The end result is that you will have a viable Grub menu to get to your Windows partition if it is still recognisable by Linux. If it is not, then the whole Windows partition is trashed. In which case, do the following paragraphs, but you will need to borrow someone's Windows installation CD. I suggest a version of Windows that does not need to be activated over the Internet. Windows 2000 is a good version of Windows and does pretty much everything that XP does and it does not have to be activated or registered, and it is still supported by Micro$oft.

Here's the problem. This situation occurs when setting up a Windows machine for dual booting to Linux. Part of Grub gets installed in physical disk sectors 0 and 1 on track 0 side 0. Even if you had your Windows install CD, the Windows install does not clear out or over-write all of the Grub stuff. So when you start your computer, you get the error that you are getting. At least this is true for Windows versions older than Vista. I don't know about Vista. I've never used or installed it.

Here's the fix - I've run into this problem a hundred times, and every time I have to use a disk editor, like Norton's DiskEdit, to zero-out those two sectors mentioned above.  Then I can successfully install Windows. If you do not have a disk editor program that can write to absolute sectors in hex (binary) on your hard drive, then go to [www.tucows.com](www.tucows.com) and search for a disk editor. I know they are around for free. HOWEVER, since you have no Windows install CD's, this is not an option for you. I write it here for information only, or in case your Windows partition is trashed. You might also consider giving up Windows. You'll be happier in the long run and have more jingle in your pocket. But, I suspect you do not want to hear that at this moment.

In any case, I wish you the best of luck and I hope you can salvage your Windows partition.

Somebody else may have a more elegant solution to this problem, and if they do, maybe they will be kind enough to post it.

~jiangshi

---

