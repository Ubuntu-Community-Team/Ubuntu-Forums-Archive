---
title: "USB HDD not recognized anymore"
date: 2009-04-10
forum: General Help
---

### Post by antimatter on 2009-04-10
Hello! I've got a problem with my usb hdd. i formatted it to FAT on my windows vista computer and copied files onto it. then i took it over to my ubuntu pc and copied some more files onto it. then after that i took it back to my windows vista computer and its kinda of inoperable now. i can see it listed under devices but when i click on the icon to open the explorer of the drive it just wont do anything. won't display free space or anything either. it does however still work under ubuntu. how do i fix this? i cant even right click and format it under vista. what happened here? any help appreciated!

---

### Post by 0cton on 2009-04-10
backup your hdd under ubuntu
than reformat it under vista (or ubuntu as fat32)
and dont use FAT
ubuntu can write stuff to it like 2 folder like A and a (even under ntsf linux systems can do that) while windows cant and so it may end up corrupted (casue of differences between linux and windows)
format it under NTFS or fat32 and it shoudl work (backup first)

---

### Post by antimatter on 2009-04-10
well... that is incredibly unfortunate and stupid. i got like 300gb of data on there. and a 60gb in my linux laptop. i mean. i used this hdd for doing backups. cant make backups of my backups without space. the fs i formated it was actually ntfs for some reason(thats what linux tells me). does that change anything?

---

### Post by coffeecat on 2009-04-10
First thing. If Vista formatted your drive as what you call FAT, then it would be FAT32. The original FAT (now referred to as FAT12) was for floppy drives. [See here]("http://en.wikipedia.org/wiki/File_Allocation_Table").

Second: if Ubuntu is telling you that the filesystem is NTFS, then that's most likely what it is. NTFS and FAT32 are different. NTFS is a later filesystem, superior to FAT32. How is Linux telling you that it is NTFS?

Third: this sounds more like a problem in Vista than a problem with the drive. NTFS is a Microsoft filesystem. If a NTFS filesystem gets damaged or uncleanly unmounted, then Windows will usually mount it and clean it up, but Linux will refuse to mount it and give you an error message. The fact that Ubuntu is mounting it means it is not damaged. The fault may be with Vista.

Have you tried rebooting Vista and trying to mount the drive again? 


**Edit:** another thought. When you see the drive listed under devices in Vista, does it give it a Windows-type drive letter? D: or E: or whatever? If so, with the drive plugged into Vista, open a Vista command prompt (no, I don't know where to find it) and issue this command:

```
chkdsk E: /f /r
```Substitute the correct drive letter for E:. The /f option fixes any errors on the drive. The /r fixes any bad blocks, so worth running as well. It will take a long time. Go and have a meal while it's running.

---

### Post by antimatter on 2009-04-10
yea i thought i formatted it to fat32 for compatibility reasons. guess i did not. i rebooted a bunch of times. it gets mounted in windows. however. if i double click the drive, explorer crashes. so i cant reformat or do anything via that. this is making me really mad :X

---

### Post by coffeecat on 2009-04-10
Look at my edit. I posted that just at the same time as you last posted. I can't promise anything, but a chkdsk might be the answer. You don't have to double-click the drive in the explorer window before doing a chkdsk.

---

### Post by antimatter on 2009-04-10
i didnt see that but i do know. yes im getting a letter. gonna try chkdsk now. good point. totally forgot that existed

---

### Post by antimatter on 2009-04-11
it finished and didnt give me any errors but that still didnt fix it.

---

### Post by N_Nick on 2009-04-11
Looks like others have similar problems. 

> [http://ubuntuforums.org/showthread.php?t=903838](http://ubuntuforums.org/showthread.php?t=903838)

You could try some of the suggestions there.

Do you see your HD as "RAW" in Vista too?

---

### Post by coffeecat on 2009-04-11
And if you google <vista raw ntfs> you come up with quite a bit more.

Two interesting ones:

[http://forum.ntfs-3g.org/viewtopic.php?f=2&t=1097](http://forum.ntfs-3g.org/viewtopic.php?f=2&t=1097)

[http://forum.ntfs-3g.org/viewtopic.php?t=634&highlight=vista](http://forum.ntfs-3g.org/viewtopic.php?t=634&highlight=vista)

This does seem to be a Vista "feature" after the filesystem has been written to by the Linux ntfs-3g driver, with XP not having any problems. 

**antimatter**, I can't see a fix there, but if you search that ntfs-3g forum there might be a real explanation for what's going on, and possibly a definitive fix. As far as I can see, that's only speculation in those two threads.


**Edit** Try this in google: site:forum.ntfs-3g.org vista raw ntfs 

That'll keep you busy. :(

---

### Post by antimatter on 2009-04-11
hmmmm yeah. they have the same problem i have but no solution either. guess ill somehow have to back up all the stuff on this hdd and then reformat. i wonder if this could happen again if i reformat it to FAT32 next time cause the problem seems to ntfs-3g related. thanks for your help guys :)

---

### Post by coffeecat on 2009-04-11
> **antimatter said:**
>  i wonder if this could happen again if i reformat it to FAT32 next time cause the problem seems to ntfs-3g related.

It's a bit of a philosophical point whether it's ntfs-3g or Vista related. :p

I'm sure you know this, but with 300GB of data, have you got any files larger than 4GB, such as video files? The maximum filesize in FAT32 is only 4GB.

---

### Post by antimatter on 2009-04-11
well yea. thats true. but it was ubuntu thats been tampering with my filesystem making it somehow unreadable for vista. what role vista plays in this is still pretty unclear though. the problem could be on both ends. whatever!  yea im aware of the filesize limit and its not a problem :) thanks for the tip though):P

---

