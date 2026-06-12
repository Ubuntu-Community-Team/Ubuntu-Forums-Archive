---
title: "Ubuntu May Have Killed My Dell E510"
date: 2008-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jay_everyday on 2008-06-16
*Ahem*
Hi Everyone, first time poster long time reader. So for the last week or so, I've read more and more about ubuntu and other linux apps and have been interested for quite some time in installing it and running it on my PC. Friday, (the 13th) I took the plunge. I downloaded the disk from Ubuntu.com and began the install. Instead of partitioning, I loaded the OS into an external HD to preserve my main HD space. During the install everything went fine and it gave me the option to dual boot. After the install it gave me Error 21 please wait... So, as a good student who was told to follow instructions, I waited but nothing happened. 

Now my PC won't boot XP, it won't boot ubuntu and I may be left without an OS. My potential solutions were as follows:
1. Boot from USB Ext. HD
2. Boot from CD
3. Boot from Main HD
4. Swap the Boot Order
5. Make sure the USB was turned on in the BIOS
6. Install the USB ext HD as a 2nd HD in the system and boot from that. 
7. Boot from XP OS Partition in Main HD. 
8. Turn off Main HD, CD, and boot solely from Ext. HD in Main HD slot.

No dice. Ubuntu may have killed my PC. If you have any suggestions on how to save my PC...or potential funeral processions for such an occasion, it would be appreciated.

Thank you.

---

### Post by LeoSolaris on 2008-06-16
Booting from a USB hard drive, from what I have read, a little more involved that the simple installation Ubuntu's installer does. Ubiquity is simply not equipped to handle that yet. (Although they may do it in the future, since distros like puppy already have an installer that handles persistant, hardware independant installs on USB drives. (I have puppy on a USB mp3 player.)

Can you boot with the LiveCD? If so, boot it up and check to see where the partitions are. Obviously Grub is installed on the internal hard drive in the MBR otherwise your error code would be a lot different.

I know it may be a little cramped, but you can make a small partition on your internal hard drive for Ubuntu and XP, then use the external for storage. 

The problem is the part of Grub on the MBR is not actually enough to boot the system by itself, and I am not even sure if it has access to USB to get the rest of the information it needs, like Grub's menu.lst amoung other things. Basicly what that error is saying is that there is no hard drive.

Using a USB hard drive as a static Ubuntu installation is tricky, more so if you want to use it on more than one system. 

My vote is to boot from the LiveCD, shrink your Xp down say 8-10 gigs, then install Ubuntu there.

---

### Post by sam_delta on 2008-06-16
as the previous post sayd, grub needs its necessary files to boot, and yes, those files are in the ubuntu parition. 
since you installed in an external harddrive, your computer is not able to see your hard drive at boot time, so it cannot access necesary grub files.

your solutions right now are 

to restore the MBR, using super grub disk @ [www.supergrubdisk.org](www.supergrubdisk.org)

restore MBR by booting into windows recovery console (using windows CD) and typing
"fixmbr" (this will restore windows bootloader, you wont be able to boot into ubuntu)

install ubuntu on the main drive double booting with XP, it will overide MBR, resulting in a new fixed MBR, but you need to install it in the main drive, as suggested by the above poster

sam

---

