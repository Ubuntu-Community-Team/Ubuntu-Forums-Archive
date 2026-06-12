---
title: "Please help with Grub rescue"
date: 2010-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AmberEven on 2010-04-03
Please bare with me if there is already a thread about my problem, and please let me know the link.  I have done search and did not find it.

I have made several mistakes in a row, which got my PC stuck.

I have windows XP on a Dell PC (64bit).  I had Ubuntu 8.10 installed as dual boot system.  I decided to delete Ubuntu from windows, which I have done before.  As a beginner, I made a mistake by not reading others' instructions one more time before I did anything.  

I deleted the partition of Unbuntu from Windows, then tried to expand the Windows partition to the free space, using a free partition manager.  Then I restarted the PC, since the software asked me to do.  This was a mistake, as I saw the message of 'Error, Grub...' and the computer could not start.  So far I guess this is still a solvable problem. 

So I took a XP service pack 2 cd, and boot the computer from cd. I thought I could then edit the Grub, as some others have suggested here.  I had done this before and it worked. 

However, this time it was different.  It asked me first to insert the automatic recovery disk into the floppy drive.  I did not have one, so I let the system to go ahead.  Then after a while, it became a blue screen with a paragraph:
" Windows is shut down to avoid damage to the computer. I may have installed new hard drives or I have a hard drive controllers. "

How can I reboot the PC now?  I assume it is the partition manager that is the 'hard drive controller that caused the problem? 

Any suggestions are appreciated.  Many many thanks!

---

### Post by Naitsirhc Hsem on 2010-04-03
You screwed up your master boot record AKA MBR.  boot with the windows xp install disk.  hit the key to repair once all of the files are loaded.  from there select your hard drive and type in the admin password.  once you reach command line type in "fixboot" hit enter and then type in "fixmbr", both without quotes.  once those commands run, reboot the computer.  

This happens to everyone once and a while.  Grub was your boot loader for your hard drive that used a file on the linux partition and had overwriten your windows mbr.  part of grub was deleted when you deleted the partition.  the commands will replace your grub mbr with the default windows mbr.

hope I could help!

---

### Post by AmberEven on 2010-04-03
Many thanks!  Will give it a try .

---

### Post by AmberEven on 2010-04-03
It worked like a charm!  Turned out that I was using the wrong reinstallation CD two.  I had two, one is for XP, the other one is for XP 64 bit, which I should have used.  

Thank you so much, [Naitsirhc Hsem]("http://ubuntuforums.org/member.php?u=1044364")!

---

### Post by Naitsirhc Hsem on 2010-04-04
No problem, any time :p

---

