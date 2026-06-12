---
title: "Urgent: Cannot start Comupter GRUB loading Error 17"
date: 2009-01-03
forum: General Help
---

### Post by ad.madhavan on 2009-01-03
I have a Dell Dimension 3100. I used to have Ubuntu 7.10 and Windows XP Dual boot working perfectly. Recently I have been running out of disk space. So I used partition magic and formatted all the partitions reserved for linux, but leaving windows intact. After which, I converted it to NTFS and merged it all into one disk space for windows.

When I tried restarting the computer I get this message:

GRUB loading Error 17

I have a lot of inportant files on the Harddrive. I do not want to loose them. Please help me restore the system or boot into windows without any file loss.

Thanks in advance, this is quite urgent since I have only one computer and life without computers can be hard....

Adarsh

---

### Post by Tim Sharitt on 2009-01-03
The grub files were on the linux disk you deleted. You need boot from your Windows CD and run fixmbr from the recovery console.

---

### Post by stderr on 2009-01-03
As the above poster says.

You only have one Master Boot Record on a hard drive, and it's small - so it usually just links to the rest of the bootloader, located elsewhere. If you installed Windows first, the MBR would have been filled with part of Windows' bootloader. Ubuntu's installation would have removed that and filled it with part of the GRUB bootloader. So, currently, a bit of the GRUB loader (basically a link to the rest of the loader - which is now deleted) resides in the MBR, and when you try to boot, the GRUB loader moans that it can't find the rest of GRUB ('cos it's gone :)). fixmbr should replace that GRUB code with Windows' own once more.

---

### Post by x22 on 2009-01-03
"fdisk /mbr" rewrites the original master boot record:
 here's a link to more info

[http://answers.google.com/answers/threadview/id/215902.html](http://answers.google.com/answers/threadview/id/215902.html)

---

### Post by ad.madhavan on 2009-01-06
Thank you very much for the answers, it is very hard to find the XP CD since Dell does not provide it with the computer anymore. I will try your suggestion when I acquire a XP Cd and hopefully it works.

---

### Post by caljohnsmith on 2009-01-06
> **ad.madhavan said:**
> Thank you very much for the answers, it is very hard to find the XP CD since Dell does not provide it with the computer anymore. I will try your suggestion when I acquire a XP Cd and hopefully it works.
If you want, you could install a Windows equivalent MBR from your Live CD so that you don't have to hunt down a Windows CD to use. You can do that by running the following commands in a terminal (Applications > Accessories > Terminal):
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And assuming the Windows partition still has the boot flag set on it, you should be able to boot straight into Windows after doing the above commands. If you decide to do it this way, let me know how it goes or if you run into problems.

---

### Post by ad.madhavan on 2009-01-08
I have finally acquired a Windows Xp CD from a friend, I will try executing fixmbr tonight and then let you know how it goes. Let us hope it works out.

---

### Post by ad.madhavan on 2009-01-09
Just figured out that there is a BIOS lock and hence need to use the OEM CD

---

### Post by trucker33377 on 2009-01-09
if you can google supergrub DL and make a cd you should be able to get into windows from that

---

### Post by ad.madhavan on 2009-01-14
Dell shipped the OEM CD, I tried to run the CD and it says 'No bootable device available'. So I called Dell, they said that the harddrive is corrupted or the CD rom is not working. So I ran the OEM Diagnostic CD that Dell provided me and tested the harddrive and the CD --- they both passed the tests. So I called Dell back. They made me run some more tests and said they will ship another Windows XP SP2 CD, and apologised for sending a faulty CD. So I am still waiting. I will keep you guys updated on the status of the problem. Also any solution to my problem that requires burning of a CD is undoable since the only one working computer I have is dead...:(

---

### Post by ad.madhavan on 2009-01-16
Ok problem solved, I was going to wait for Dell to ship the CD but they said it will take another week, so I went and hunted down a Ubuntu CD from a friend and used just as caljohnsmith advised. It works!. Thank you very much caljohnsmith.

:)

---

### Post by ad.madhavan on 2009-01-22
So...I finally got my computer to work. I got fed up of waiting for puralator so I just borrowed Ubuntu8.10 from a friend and used caljohnsmith's method. It worked! Thank you very much for you replies.

---

### Post by ad.madhavan on 2009-01-22
Now, how do mark this thread as solved?

---

### Post by drakoumel on 2009-08-19
guyz got the same problem but i cant do anything of those u say.. 
i disabled my 2nd disk (ubuntu on ) and let pc boot from disk 1 ( xp on ) but i get the same problem again why? 
i tried booting hirens CD and same problem it wont let me boot anything else.. 
i did change the boot to DVD from the bios any help?

---

