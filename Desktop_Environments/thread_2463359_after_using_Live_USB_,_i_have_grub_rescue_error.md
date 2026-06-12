---
title: "after using Live USB , i have grub rescue error"
date: 2021-06-09
forum: Desktop Environments
---

### Post by java884 on 2021-06-09
hi,
i have a computer with ubuntu 20 installed like OS ,  with live USB (other debian os) i modified  some files  in my ubuntu Desktop on my computer  partition, after that when i want to turn on my my computer i have error message "grub rescue"
thanks for readind

---

### Post by sudodus on 2021-06-09
Please describe with many more details what you have and what you did. Otherwise it will be next to impossible to guess what is the problem.

---

### Post by java884 on 2021-06-09
i modified a personnal file myfile.txt with live usb  after that i want to turn on my computer with ubuntu , i have message error '/boot/grub/i386-pc/normal.mod/ not found,
i do the same thing with other computer i have the same message

---

### Post by java884 on 2021-06-09
> **sudodus said:**
> Please describe with many more details what you have and what you did. Otherwise it will be next to impossible to guess what is the problem.

		 				 				 		 			 				[INDENT] 					i use a famous live usb for anonymity and i changed a personal file  in my Desktop folder , whent i  want to turn on my computer with ubuntu  , i have black screen with command line welcome to grub . error unknown  file system
grub rescue>
after that i find in forum ubunutu
[https://askubuntu.com/questions/1423...em-grub-rescue]("https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue")
i do this
grub rescue> set prefix=(hd0,msdos1)/boot/grub
grub rescue> insmod normal
 error:file '/boot/grub/i386-pc/normal.mod'not found 				[/INDENT]

---

### Post by ajgreeny on 2021-06-09
Where exactly was the myfile.txt in the filesystem and what was it for, if anything?
Has it anything to so with the OS itself or was it a file in your home.
If it was a text file that was not in the filesystem of the installed root partition there is no way that a simple edit should affect anything to do with grub.

Are you certain that you did not carry out any other changes to system files while using the live OS on USB?

[COLOR="#FF0000"]EDIT:[/COLOR]
I have just seen the post above, which you must have been writing when I started this post.

All those commands shown  "set prefix" etc etc presuppose that your filesystem is on disk in the way that you have shown there, about which we know nothing.

It assumes you have the OS on the first partition of the first disk in the computer, and also, I think, that it is a 32bit system and is using legacy BIOS, not UEFI.
Did you take account of all of that when attempting to boot that way from grub rescue> ?

---

### Post by java884 on 2021-06-10
i think this live USB use encrypting mode when adding  or updating a file, i have 2 computer one with bios and other one with UEFI , i have gub rescue  with filesystem not found

---

### Post by yancek on 2021-06-10
As pointed out above, modifying a 'personal' file which you created in your /home/user/Desktop directory should have no effect on Grub.

Boot the live usb you have and when you are at the grub rescur, run the following command for each Linux filesystem partition you have to see if you can find the normal.mod file:

grub rescue> ls (hd0,msdos1)/boot/grub/i386-pc/

If you can't find it, you need to determine which is your root filesysem partition and navigate to /usr/lib/grub/i386-pc and find the normal.mod file and copy it to the  directory in /boot/grub/i386-pc  This is only on the computer which is not EFI

If you are now getting a different error (unknown filesystem) run the following command from the live usb you are using and post the output here indicating which drive and partition is the root filesystem partition.

```
sudo fdisk -l
```

---

### Post by grahammechanical on 2021-06-10
The command

```
insmod normal
```

is supposed to take grub out of rescue mode and into normal mode.

[https://www.linux.org/threads/understanding-the-various-grub-modules.11142/](https://www.linux.org/threads/understanding-the-various-grub-modules.11142/)

If the file is not found it is because the path is incorrect. There are 285 modules in the /boot/grub/i386-pc directory. For some reason that I cannot understand they are all in the Amiga SoundTracker audio format.

An irrelevant piece of information, I admit. But apparently to get Grub out of rescue mode we need that normal.mod file to load and for that to happen the path to the Grub folder needs to be correct. If we haven't corrected the problem that put Grub into rescue mode in the first place we still may not get to a desktop.

I have more than one install of Ubuntu on my machine and I find it more convenient when I mess up to the point that Grub loads into rescue mode to use one of the other installs of Ubuntu while I plan a re-install of the broken OS. Which is what I had to do a week ago when the desktop blinked out of existence while the browser was loading a newspaper page and I was left with a black screen with error messages repeated line after line.

Regards

---

### Post by oldfred on 2021-06-10
Often the error is from booting with an old install of grub in wrong boot mode. 
Or system is UEFI but you have an old BIOS boot install of grub in MBR. Or vice-versa.
Check your boot mode in UEFI/BIOS and be sure it matches your install.

Otherwise:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by java884 on 2021-06-11
first i will say thinks for helping me 
when i tape ls (hd0,msdos1)/boot/grub/i386-pc/
error  file '/boot/grub/i386-pc/' not found

---

### Post by java884 on 2021-06-11
> **yancek said:**
> As pointed out above, modifying a 'personal' file which you created in your /home/user/Desktop directory should have no effect on Grub.

Boot the live usb you have and when you are at the grub rescur, run the following command for each Linux filesystem partition you have to see if you can find the normal.mod file:

grub rescue> ls (hd0,msdos1)/boot/grub/i386-pc/

If you can't find it, you need to determine which is your root filesysem partition and navigate to /usr/lib/grub/i386-pc and find the normal.mod file and copy it to the  directory in /boot/grub/i386-pc  This is only on the computer which is not EFI

If you are now getting a different error (unknown filesystem) run the following command from the live usb you are using and post the output here indicating which drive and partition is the root filesystem partition.

```
sudo fdisk -l
```

first i will say thinks for helping me 
when i tape ls (hd0,msdos1)/boot/grub/i386-pc/
error  file '/boot/grub/i386-pc/' not found 				

for fdisk -l i get
disklabel type:  dos

device                    Boot              start             size                            type
/dev/sda1                *                      2048           240.08 G                 linux

---

### Post by java884 on 2021-06-11
> **grahammechanical said:**
> The command

```
insmod normal
```

is supposed to take grub out of rescue mode and into normal mode.

[https://www.linux.org/threads/understanding-the-various-grub-modules.11142/](https://www.linux.org/threads/understanding-the-various-grub-modules.11142/)

If the file is not found it is because the path is incorrect. There are 285 modules in the /boot/grub/i386-pc directory. For some reason that I cannot understand they are all in the Amiga SoundTracker audio format.

An irrelevant piece of information, I admit. But apparently to get Grub out of rescue mode we need that normal.mod file to load and for that to happen the path to the Grub folder needs to be correct. If we haven't corrected the problem that put Grub into rescue mode in the first place we still may not get to a desktop.

I have more than one install of Ubuntu on my machine and I find it more convenient when I mess up to the point that Grub loads into rescue mode to use one of the other installs of Ubuntu while I plan a re-install of the broken OS. Which is what I had to do a week ago when the desktop blinked out of existence while the browser was loading a newspaper page and I was left with a black screen with error messages repeated line after line.

Regards


thanks for your help the link is very good  i'm looking also for some learning about grub it's a good help , i'd like to understand more about grub that why i will  re-install broken OS at last option

---

### Post by yancek on 2021-06-12
Did you get the output you posted in post 11 from your live usb?  If so, it should show at least 2 drives, the usb you are using and the internal hard drive on which you have Ubuntu.  Post the entire output of fdisk command.

Do you have only one partition on the drive on which you installed Ubuntu?  If you run ls from the grub rescue do you see only one drive/partition?  Is this computer older and using Legacy BIOS rather than EFI?  If the error still is normal.mod not found, have you tried to copy it from the /usr/lib/grub/i386-pc directory?

---

