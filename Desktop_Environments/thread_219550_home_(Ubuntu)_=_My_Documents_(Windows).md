---
title: "home (Ubuntu) = My Documents (Windows)"
date: 2006-07-20
forum: Desktop Environments
---

### Post by escamillo on 2006-07-20
I want to configure Ubuntu and Windows in a way that they both use the same home/My Documents folder. My System has two harddisks, on the first there are three partitions: one with Windows on it (NTFS), one with Ubuntu on it (ext3) and the swap partition. The second harddisk has just one NTFS partition. I want to put the home directories and the my documents directories of all users of this computer on this harddisk, so that /home/user01 equals the My Documents folder of user01 in Windows. Is that possible?

How can I mount an NTFS partition in Ubuntu. When I try to open it, Ubuntu says that it cannot be mounted.

---

### Post by adam.tropics on 2006-07-20
I think you may need to look into this a little further as writing to ntfs is awkward to say the least. Added to that I am not sure that sharing /home as My Documents is incredibly sound as an idea either. A folder within /home perhaps but I really wouldn't want windows to have access to all the stuff in my /home directory, too much there to stuff up! Anyway, [a starting point.]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs")

---

### Post by escamillo on 2006-07-20
Would it be better if I formatted the partition with FAT32?

---

### Post by timetunnel on 2006-07-20
I woulnd't do it:
[LIST]
[*]NTFS has no write support in Linux.
[*]FAT32 is a file system that can be used by Windows and Linux, but it doesn't support some features of a Linux file system (user permissions, among others).
[*]"home/user01" is not the same as "My Documents" on Windows. That would be something like ""home/user01/MyDocuments". "home/user01" contains a lot of user-specific configuration files and a lot of stuff that Windows scatters across several subdirectories in your Windows home folder ("..Documents and Settings\username"). I guess it just wouldn't work to have the whole folder on a FAT32 partition.
[/LIST]

What I would do is:[LIST=1]
[*]Use FAT32 instead of NTFS
[*]Create a folder "MyDocuments" on that partition
[*]Point Windows to that folder as the standard "My Documents" folder (no idea how to do that, but I've read somewhere you can change the settings for that in the Registry)
[*]In Linux, mount the FAT32 partition to folder "home/user01/MyDocuments"
[/LIST]
I guess that's all to do to make that work.

---

### Post by escamillo on 2006-07-20
@timetunnel: Using your method sounds reasonable. I know how to do points 1-3 but how do I mount the FAT32 partition to home/user01/MyDocuments? (Sorry, I'm quite a Linux-newbie.)

---

### Post by timetunnel on 2006-07-20
I'm at work right now (no Linux here) but can post details for mounting FAT32 later. Or maybe someone else can help?

---

### Post by blueturtl on 2006-07-20
> 
3. Point Windows to that folder as the standard "My Documents" folder (no idea how to do that, but I've read somewhere you can change the settings for that in the Registry)


To change the location of your My Documents folder install TweakUI. Under TweakUI there was a tab that allowed changing the locations of some of Windows special folders. I have not tested this under Windows2000 or XP, but it worked fine in Windows 95/98.

---

### Post by glinsvad on 2006-07-20
Like timetunnel suggested, I have a FAT32 partition containing my Documents folder. After I had redirected WinXP I merely mount the FAT32 partition in /media/storage or some such. Then I create a symbolic link from /home/username in the terminal:
```

ln -s /media/storage/Documents Documents

```

This works excellent. The Documents folder will even show up in the Places-menu, and you can have it shown on the desktop too:

Either start Applications->System Tools->Configuration Editor and locate the key /apps/nautilus/desktop/documents_icon_visible and set it to true.

or 

In terminal just type:
```

conftool-2 --type bool --set /apps/nautilus/desktop/documents_icon_visible true

```

---

### Post by glinsvad on 2006-07-20
> 
To change the location of your My Documents folder install TweakUI. Under TweakUI there was a tab that allowed changing the locations of some of Windows special folders. I have not tested this under Windows2000 or XP, but it worked fine in Windows 95/98.


In WinXP you can simply rightclick My Documents and then type in another location in the Target-tab

---

### Post by moma on 2006-07-20
Hello all,

1) Actually Linux has recently gained full NTFS read and write support. The driver (ntfs-3g) is in beta (test phase) but reports say it is reliable and quick.

We had a note about ntfs-3g in our local Linux forum ( [http://linux1.no/node/1849]("http://linux1.no/node/1849") ). Follow the links to articles on SourceForge.net  and OSnews.com.

Study also this thread
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=open+source+ntfs]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=open+source+ntfs")
------------------------------

2) Sharing a FAT32 partition Linux and Windows might be a better and proved solution. Take a look at this guide on howto mount FAT partition in Linux.

[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")
Browse to chapter 15.
------------------------------

3) A third and popular solution is to share an ext2 filesystem between Linux and Windows. Use this driver in Windows [http://www.fs-driver.org]("http://www.fs-driver.org/")
Drawback: The driver is not open source (shareware or something)
------------------------------

More Ubuntu stuff here
[http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

Cheers,
  moma
  [http://www.futuredesktop.com/AsteriskPBX.html](http://www.futuredesktop.com/AsteriskPBX.html) 
  :)

---

### Post by escamillo on 2006-07-20
Here is what I've done up top now:

- I reformated the NTFS partition to FAT32
- I mounted the FAT32 partition
- I created "D:\Dokumente und Einstellungen\[Username]\Eigene Dateien" for each user and created a symbolic link in each user's home directory

Now I would like to
- remove (or make invisible) the icon of the mounted partition on the desktop (just this partition - other mounted volumes, like CD Drive, external HD etc still should appear there) 
- make the "Eigene Dateien" folder of each user appear in the Places-menu and the desktop
- make it the default folder which is presented to the user by default when he wants to save something

---

### Post by kurniawands on 2006-07-26
definitely agree with what momma said... use ntfs-3g. works fine with me. been doing read/write and haven't seen any problem...:-D wish i can say "never"... amen.

---

### Post by teasum on 2006-08-01
I used the ext3 driver from fs-driver.org to allow XP to read/write to my linux partitions.  Then, I created a folder within my /home/user directory for 'documents', and used TweakUI to point XP to that folder.  I also linked up "My Music", "My Videos", etc.  Practically, it works well... philosophically, it was nice to make Windows conform to Linux, and not the other way around.

Another cool thing you can try (at your own risk, of course) is to point your XP Desktop folder to your Ubuntu Desktop folder.  So far, it's working allright for me, and I now have the same desktop items in both XP and Ubuntu, not counting the special links (i.e. my computer in XP, mounted drives in Ubuntu).

Finally, if you really want to link things up, I highly recommend configuring Thunderbird and Firefox to use the same profile in both XP and Ubuntu (assuming you use these programs in XP and Ubuntu).  Try the following link: [http://www.ubuntuforums.org/showthread.php?t=203524](http://www.ubuntuforums.org/showthread.php?t=203524).

That's just my 2 cents worth.

---

