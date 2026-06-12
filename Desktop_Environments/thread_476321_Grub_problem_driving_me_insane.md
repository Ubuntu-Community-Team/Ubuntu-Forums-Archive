---
title: "Grub problem driving me insane"
date: 2007-06-17
forum: Desktop Environments
---

### Post by scrime on 2007-06-17
Hi everyone, I have a slight problem with a dual booting system.  I use Grub to give me the option to start either Windoze or Ubuntu.  I installed some Windoze updates and now Grub dissapeared and it boots directly into Windoze.  I re-installed Grub through the alternative Ubuntu Feisty 7.04 CD and the Grub boot menu comes up as it was.  When I select Ubuntu it says "No partition found" so what i did was, pressed e for edit, I changed the root to (hd0,1), for some reason this works and it starts up Ubuntu normally.  If I go into the console and type "sudo grub" "find /boot/grub/stage1" it ouputs "(hd1,1)" which is the same as my Ubuntu entry in my "menu.lst". (hd1,1) doesn't boot into grub so I changed my "menu.lst" to (hd0,1) which starts up Ubuntu everytime.  The problem is whether I start Windows as (hd0,0) or (hd1,0) it doesn't work.  It say's "NTLDR is missing press Ctrl + Alt + Del" after doing so, Grub is gone and Windows comes up immediatly.  I then need to repeat the process if I want to go into Linux.  It is seriously annoying.  What can I do, I've downloaded so much Synaptic packages that I'll be very upset if I have to re-install Ubuntu.

---

### Post by WakkiTabakki on 2007-06-17
All you need to do is re-install the boot manager, check this one out:
[http://ubuntuforums.org/showthread.php?p=815810#post815810](http://ubuntuforums.org/showthread.php?p=815810#post815810)

Good luck
/N

---

### Post by scrime on 2007-06-17
Thanks for the reply.  Will try now and let you know the results.

---

### Post by scrime on 2007-06-17
OK, I back in Ubutu after restoring grub, still with the same problem though.  I type 
¨sudo fdisk -l¨. This is the output i get:

> scrime@ubuntu-scrime:~$ sudo fdisk -l
Password:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19929   160079661    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1530    12289693+   7  HPFS/NTFS
/dev/sdb2   *        1531        2500     7791525   83  Linux
/dev/sdb3            2501       24320   175269150    f  W95 Ext'd (LBA)
/dev/sdb5            2551       24320   174867493+   7  HPFS/NTFS
/dev/sdb6            2501        2550      401562   82  Linux swap / Solaris

Partition table entries are not in disk order


I just thought maybe that boot flag on sda1 is the problem, I want it to find grub on sdb2, would that be (hd0,1)?  sdb3 is a bit worrying, I sure that should be NTFS.  Could ¨Partition table entries are not in disk order¨ be a problem?

---

### Post by scrime on 2007-06-17
This is the entry in my menu.lst which starts up ubuntu succesfully.

> title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f70416f4-4aa1-43f9-91a0-74efb009b1fc ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

This is the entry in my menu.lst which doesn´t start Windows successfully.

> title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by scrime on 2007-06-17
Before everything went wrong (hd1,1) was what started up Ubuntu correctly and (hd1,0) started Windows correctly.

---

### Post by scrime on 2007-06-17
I typed ¨sudo grub¨

then

> 
grub> find /boot/grub/stage1
 (hd1,1)

---

### Post by scrime on 2007-06-17
Still having a problem, at least it&#347; improved.  Grub now starts up everytime no matter what I do, changed Ubuntu to start up as (hd1,1).  Windows however wont start whether I try to start it as (hd0,0) or (hd1,0).  My fdisk output stays the same.  Any help would be appreciated.

---

### Post by jjross on 2007-06-17
Do a little research on Grub, I think you will find that stage 1 is actually on the partition where Ubuntu is
This is a file that grub refers to  for the information it needs.
So to recap this, Grub is on your MBR but stage 1 is on your ubuntu partition, this seems to cause some confusion sometimes.
Hope this helps.
look at this link
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by jimbo99 on 2007-06-17
How are you changing the values of your menu.lst file?  Are you doing it manually or are you using the grub setup command?

the find command is correct.  It is telling you the correct location.  But the setup command fails sometimes.  Well, actually every time on my computers.  So I go in and manually edit the menu.lst file to ensure that it has the correct value identified by the find command in grub.

---

### Post by scrime on 2007-06-19
Thats the weird thing, I tried both editing the menu.lst and did grub setup.  grub find command outputs (hd1,1) although (hd0,1) starts Ubuntu.  Ubuntu used to be started with (hd1,1) and Windows with (hd1,0).  Windows no longer starts at all, Ubuntu starts with (hd0,1).  The problem occurred after Windows randomly overwrote my MBR, I reinstalled grub and was left with this issue.

I hoping someone could look at my fdisk output and tell me what Im doing wrong.  I hope it&#347; not starting to get confusing but although I dont prefer to use Windows I need for my studies (MCSE).  Maybe i should just re-install Windows.  Re-do grub, hopefully that'll work.

---

### Post by vexorian on 2007-06-19
windows doesn't randomly overwrite MBR,  if it wasn't the windows installer CD then it could have been a virus or a physycal flaw in the hard drive.

As a matter of fact, NTLDR is missing press Ctrl + Alt + Del is a problem I got myself, make sure a system file called NTLDR is in your C: partition, if it is then your grub is pointing to the wrong partition, if there isn't then something bad is corrupting your windows.

PS: NTLDR is often hidden and marked as a system file, so it might be hard to verify it is there.

---

### Post by scrime on 2007-06-19
Thanks, did check drive seems to read fine, i do have the NTLDR. Thank goodness got a bit of a fright there.

I reading an informative article on grub at the moment
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=237511]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=237511")

I will solve this and reply.

---

