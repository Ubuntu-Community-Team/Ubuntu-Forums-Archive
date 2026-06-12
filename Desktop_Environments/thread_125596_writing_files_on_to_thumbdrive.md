---
title: "writing files on to thumbdrive"
date: 2006-02-04
forum: Desktop Environments
---

### Post by krait on 2006-02-04
hi,

this is somethin rather strange. i m runnin breezy. my thumbdrive is instantly recognized wen i plug it, and files are shown. Reading is no problem. But wen i write a file onto it,  it jus does so instantaneously, no copying time, however big the file be. The thing i noticed was, the file gets written only wen i unmount the drive. Cuz i have a transparent thumb drive im able to see wen it actually gets unmounted,much after the icon vanishes frm the screen. But not all my usb s are transparent, and if i pull it out before it copies, im not able to delete it also later, a new .trash folder gets created wit an incomplete copy of the file which i cant delete also.

I d really appreciate if someone helped me wit this. I asked someone else who runs breezy on the same type f laptop, and he mentioned nothing of this sort.

cheers

---

### Post by taurus on 2006-02-04
The easiest solution right now is instead of pulling it out when you want to remove it, click on the icon and use the umount option.  That's why, the system will write whatever it needs to your thumbdrive before it unmounts it...  No need to worry about corrupt files.

---

### Post by krait on 2006-02-04
thats wat i do. I click unmount. Only then do files get copied. But the icon on the screen is removed. If my thumbdrive were not transparent, i wudnt even know this and wud be thinkin tht file copyin to usb s doesnt work on ubuntu.

cheers

---

### Post by Randomskk on 2006-02-04
How do you mean, transparant?
What can you see inside? an LED?

---

### Post by taurus on 2006-02-04
Are you telling me that it doesn't even have a little blue light on the side telling you when it's busy copying or writing???

---

### Post by krait on 2006-02-04
ya it has an led. So i m able to see wen to plug it out. But yes, my other drives dont have any sort of indication like tht. But my question, why is this the case?I have used the same thumb drives with Knoppix and Red hat, none of them gave me any such problem. Why is copyin done only wen i unmount on ubuntu alone?

cheers

---

### Post by 5-HT on 2006-02-05
The reason why data is not written immediately to the drive is that by default the drive is mounted with asynchronous I/O filesystem access (data to be written is stored in a buffer and written later on, rather than immediately).

This is actually a **really good thing** as if the drive were mounted with synchronous write abilities, it would wear out much much faster as the FAT table would get constantly rewritten with every new block allocation while a file is being written.

The important thing to remember about usb flash drives is that they have a limited number of write cycles, and therefore writing to the drive synchronously is not a good idea.


The best course of action to ensure you do not disconnect the drive in the midst of I/O is to unmount the drive via the CLI.

(I've heard mention around here that if you unmount via GUI, a dialogue says the drive's unmounted prior to the actual syncing and unmounting of the drive.)

If you wait for the prompt to return, you'll be assured (better yet, use the verbose option of umount) that the drive was unmounted sucessfully and  is safe to disconnect.



If you don't know how to do such, enter the command: ```
 mount
``` when the drive is mounted and post the results here so that someone can identify where the drive is being mounted in order to give you the correct command to unmount it.

(I set up my own fstab entry for my flash drive as I don't like the automount of removable media so I wouldn't know where it gets mounted automatically)



----------
On another note, my flash drive has an LED which blinks during  I/O but is supposed to go off completely when the drive is unmounted.

It does so under windows, but on Ubuntu the LED remains on even after unmounting... 

I'm curious if anyone else is experiencing something similar?
Thanks for any insight.


HTH

---

### Post by krait on 2006-02-08
This is what i get wen i type mount after pluggin in my usb.

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type vfat (rw,iocharset=utf8,umask=000)
/dev/hda5 on /media/hda5 type vfat (rw,iocharset=utf8,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

but i would like to know why my drive doesnt seem to work the way i said on other linux distros leave alone windows? 

thank you

cheers

[QUOTE=5-HT]The reason why data is not written immediately to the drive is that by default the drive is mounted with asynchronous I/O filesystem access (data to be written is stored in a buffer and written later on, rather than immediately).

This is actually a **really good thing** as if the drive were mounted with synchronous write abilities, it would wear out much much faster as the FAT table would get constantly rewritten with every new block allocation while a file is being written.

The important thing to remember about usb flash drives is that they have a limited number of write cycles, and therefore writing to the drive synchronously is not a good idea.


The best course of action to ensure you do not disconnect the drive in the midst of I/O is to unmount the drive via the CLI.

(I've heard mention around here that if you unmount via GUI, a dialogue says the drive's unmounted prior to the actual syncing and unmounting of the drive.)

If you wait for the prompt to return, you'll be assured (better yet, use the verbose option of umount) that the drive was unmounted sucessfully and  is safe to disconnect.



If you don't know how to do such, enter the command: ```
 mount
``` when the drive is mounted and post the results here so that someone can identify where the drive is being mounted in order to give you the correct command to unmount it.

(I set up my own fstab entry for my flash drive as I don't like the automount of removable media so I wouldn't know where it gets mounted automatically)



----------
On another note, my flash drive has an LED which blinks during  I/O but is supposed to go off completely when the drive is unmounted.

It does so under windows, but on Ubuntu the LED remains on even after unmounting... 

I'm curious if anyone else is experiencing something similar?
Thanks for any insight.


HTH[/QUOTE]

---

