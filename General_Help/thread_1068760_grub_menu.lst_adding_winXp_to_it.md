---
title: "grub menu.lst adding winXp to it"
date: 2009-02-13
forum: General Help
---

### Post by unix1adm on 2009-02-13
I just reformatted and reloaded my system with a winxp partition, 

I restored from a back up but I do not know the syntax to put in the /boot/grub/menu.lst to get it to see the new3 XP partition. 

My device is xp hda2, ubuntu hda1 and fedora hda4.  ubuntu and Fedora work fine. But i get an error on the Xp menu option. 

Can someone post the stanza I need to add for XP. 

I did a search but not finding what i need. 

Thanx

CJ

---

### Post by unix1adm on 2009-02-13
am i using the correct file too?

---

### Post by blazemore on 2009-02-13
Add a new entry
```
title           Microsoft Windows XP
root            (hd0,2)
savedefault
chainloader     +1

```

---

### Post by caljohnsmith on 2009-02-13
> **unix1adm said:**
> 
[COLOR="Blue"]My device is xp hda2[/COLOR], ubuntu hda1 and fedora hda4.  
Since Grub's numbering begins with 0 and not 1, hda2 would be (hd0,1). How about trying the following entry:
```
title Windows XP
root (hd0,1)
chainloader +1
```
Let me know if that works or not.

---

### Post by unix1adm on 2009-02-13
> **blazemore said:**
> Add a new entry
```
title           Microsoft Windows XP
root            (hd0,2)
savedefault
chainloader     +1

```


i tried that but I do not see anything in the menu list. 

I wonder why... I have the

title WindowsXP
root  (hd0,2)
savedefault
chainloader +1

Menu only shows Ubuntu
Fedora and Red hat. ( i use to have a redhat install.

I dont think I am editing the correct file...

---

### Post by unix1adm on 2009-02-13
I copied the orginal file back and incase i munged it but get the same rseults

---

### Post by unix1adm on 2009-02-13
I found this but I think I may have a bad grub ...

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

I loaded this and it shows windows in the listbut for some reason it does not show on the boot menu...

I tried this too but keep getting file not found when I use the find comand

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Kevbert on 2009-02-13
> **blazemore said:**
> Add a new entry
```
title           Microsoft Windows XP
root            (hd0,2)
savedefault
chainloader     +1

```

Go to Applications-Accessories-terminal and enter
sudo gedit /boot/grub/menu.lst
Enter your log-in password when prompted.
Look for lines that say
```
title		Other operating systems:
root 
```
Below that add the lines displayed above. You should now save the file and exit gedit and terminal.
If you now reboot everything should work. You need to edit this file for the last operating system that you installed. If it's fedora than that's where you should edit the file.

---

### Post by unix1adm on 2009-02-13
Yes I tried that but the file still did not work. So I tired several other thing and could not get the file. I am reinstalling from back up again to see if that fixes it. 

I'll post back in a few with the results.

Its like the boot loader got munged or the MBR or something.

---

### Post by unix1adm on 2009-02-13
I cannow see the menu entry but get

error 13: Invalid or unsupported executable format
Press any key to continue...

---

### Post by unix1adm on 2009-02-14
I am still looking for a solution to this...

---

### Post by blazemore on 2009-02-15
Try running
```
sudo update-grub
```

---

### Post by unix1adm on 2009-02-15
OK I did that an now I get 

windows could not start because th efollowing file is missing or ocrrupt:
<windows root> \systems32\hal.dll

Please reinstall a copy of the above file


oh ya my menu.lst looks like this

title		WindowsXP
rootnoverify		(hd0,1)
chainloader	+1

---

### Post by jocko on 2009-02-15
> **unix1adm said:**
> I cannow see the menu entry but get

error 13: Invalid or unsupported executable format
Press any key to continue...

> **unix1adm said:**
> OK I did that an now I get 

windows could not start because th efollowing file is missing or ocrrupt:
<windows root> \systems32\hal.dll

Please reinstall a copy of the above file


oh ya my menu.lst looks like this

title        WindowsXP
rootnoverify        (hd0,1)
chainloader    +1

Those errors are from the windows boot loader, not grub.
Windows needs to be on the first (visible) partition on the drive. Either find a way of hiding the ubuntu partition, or reinstall with windows on the first partition...

---

### Post by unix1adm on 2009-02-15
Windows was installed first and was th efirst 50G of the drive. So what else could it be???

---

### Post by unix1adm on 2009-02-18
So i wiped the drive out and reloaded everything. XP 0-50G fedora next and i was able to boot and see the xp. then I loaded ubuntu and now i see fedora and no xp, I get the orginal message now. 

This is what i have in my menu.lst

title	WindowsXP
root 		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by unix1adm on 2009-02-18
root@cj454-lt:/boot/grub# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d027d02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6554       20289   110334420   83  Linux
/dev/sda2               1        6553    52636941    7  HPFS/NTFS
/dev/sda3           21061       22727    13381200   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           20290       20552     2112547+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by unix1adm on 2009-02-18
i tried changing ht eline from hd(0,0) to hd(0,1) and I am back to the orginal errors about missing hall.dll 

why is this so hard to do...

---

### Post by unix1adm on 2009-02-18
I reran the update-grub and nothing get added to the file. Like grub does nnot see the windows partition???

---

### Post by jocko on 2009-02-18
> **unix1adm said:**
> I reran the update-grub and nothing get added to the file. Like grub does nnot see the windows partition???
update-grub does not look for windows, it only looks for the settings in the debian "automagic kernels list" section of menu.lst and updates the list with the kernels it can find in /boot.
> **unix1adm said:**
> root@cj454-lt:/boot/grub# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d027d02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1 [COLOR=Blue]  *[/COLOR]        6554       20289   110334420   83  Linux
[COLOR=Red]/dev/sda2               1        6553    52636941    7  HPFS/NTFS[/COLOR]
/dev/sda3           21061       22727    13381200   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           20290       20552     2112547+  82  Linux swap / Solaris

Partition table entries are not in disk order
So windows is on the first physical partition, but now that partition appears as /dev/sda2? I don't understand how that could happen, but it could be what's causing your problems.
I'm not sure what the little * next to your /sda1 partition means, but I thought that indicated that the "bootable" flag is turned on. If that's the case, your problem is that you by some reason have disabled the bootable flag on the windows partition (which needs to have it) and activated it on one of your linux partitions (which don't need it).
> **unix1adm said:**
> i tried changing ht eline from hd(0,0) to hd(0,1) and I am back to the orginal errors about missing hall.dll 

why is this so hard to do...
Again, if you get a message about missing hal.dll, that message comes from the *windows* boot loader (ntldr), not grub. So grub works correctly and hands over command to ntdlr, but some setting in ntldr is wrong (that's in the file boot.ini on the root of your windows C:\ partition).

---

### Post by unix1adm on 2009-02-18
how do i see the boot.ini if i cannot boot to windows?

i tried to mount it in linux and it says it cannot mount in was in use or something like that. Ill post the screen msg.

---

