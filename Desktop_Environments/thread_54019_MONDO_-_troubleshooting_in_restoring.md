---
title: "MONDO - troubleshooting in restoring"
date: 2005-08-03
forum: Desktop Environments
---

### Post by ::DoGG:: on 2005-08-03
Hello!
I recently installed Mondo rescue to help me manage the backups of the servers i have. Sibnce it`s a really good piece of software and i have a good experinece with it in a previous distributions i had.
So it`s like that.
I have a server with one SCSI disk /dev/sda on wichich i have 1 root partiotion and one swap partition. I made bootables iso image and to test i verified the image and everything went ok.
So i copied the iso into my windows machine and want to try launch it on WMware workstation to see if it work. The iso boots ok but after i i choose to read backup from CD i get errors that he`s unable to mount the fd0 and so on.
So i get the mountlist editor, deleted all the entries in it and let the mondo partition the drive. After mondo did the partitioning he still spits out the errors about unable to mount and keep asking me for cd #1 ( WTF ???!!!!).
Since my system drive that is backed up is 2 G and a disk that i want to restore to is 4G it`s not a matter of disk beying to small. I think i just made something wrong with the mountlist...

Anybody had a similliar experience with mondo on ubuntu ????

---

### Post by frodon on 2005-08-03
I tried mondo but it never work for me, i don't know what's the problem with my cd recorder but mondo don't manage to write with it, it search on the good drive but don't start writing (but iso file work). Also the cdrecord -scanbus command doesn't work for me (it don't give me the name of my drive). 
I'm also interresed to know someone who's got experience with mondo and ubuntu.

---

### Post by ::DoGG:: on 2005-08-03
Did You checked You iso ? did You try to restore from them ?

---

### Post by frodon on 2005-08-03
I don't check my iso because for some reasons I want only a backup dvd, I have just made  a generation test of iso to know what step is good. But I think burning the iso image should be the same than generating a backup dvd, can you confirm that ?
When I run a backup mondo try to backup all my drive and I haven't managed to run a backup only on the linux partition, have you managed it ?
However if nobody answer to this thread or if burning the iso file is the same as creating a backup dvd, i'm ok to make some tests  :wink: .

I will run an iso file generation this evening, tell me what you want to test on this iso file (how to check it) and I will give you feedback about how it works on my computer.
I have a 20Go IDE drive as master and my linux partition is 11Go.

EDIT : give me also the command that you use to run the iso file generation.

---

### Post by ::DoGG:: on 2005-08-03
If You have the ISO image, burn it in your dvd drive and You should get a bootable dvd that should restore whole your system.
If You run mondo through commandline the -E option is for excluding the paths, so for exmaple when i use
 ```
mondoarchive -Oi -9 -E "/mnt" -T /temp -D /isos
```
im telling mondoarchive to make backu to isos ( -Oi option) and to exclude from backup /mnt directory ( -E "/mnt") and i tell him to use /temp directory as a directory for his temporary files ( -T /temp ) and to write iso to /isos directory ( -D /isos ).

---

### Post by GrayMagiker on 2005-10-12
You said run 
```
mondoarchive -Oi -9 -E "/mnt" -T /temp -D /isos
```
Does this work?  I received an error message with this command.  
After I read the Man page on mondoarchive I noticed that "-d" is the option to specify a directory for the iso images and "-D" is the option to make a diferential backup.  

Also, is the "-k FAILSAFE" option needed in Ubuntu?  The documentation recommends it for Debian kernels, and Ubuntu is based on Debian so I would guess yes.  

Anyway, I have not yet gotten mondo working on Ubuntu so don't pay too much attention to what I say. I will post here and/or in a new thread when I get it working.  Until then.

---

