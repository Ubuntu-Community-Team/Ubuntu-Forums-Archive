---
title: "Ubuntu as a File Server"
date: 2006-08-05
forum: Desktop Environments
---

### Post by dadude on 2006-08-05
Hello Everyone,
This is my first post. Here's what I'm wondering I just recently installed Ubuntu on my laptop and it runs great after i used Automatix to install all my codecs. Now I need to install it on an older server that I have it has scsi hard drives. 3 18gb drive not currently in raid at all. So Here is what I want to do. I'm considering wiring up some gigabit ethernet wires. I then am going to have an external hdd connected to my server. Then save all my bit torrent files to the hdd. Via the gigabit ethernet. The external HDD will be NTFS. Then won't be a problem trying to write to it will it? 

So my main Questions:
1. Writing to external NTFS is it a problem?
2. Will the SCSI hard drives work fine with ubuntu?
3. How easy will it be to access the hdd from windows machines? What Will I need to do?

Thanks

---

### Post by iammeagain on 2006-08-05
I am not expert, but i tried using an NTFS partition and it finally got too annoying and complicated so i went with Fat32 instead, both windows and linux can read and write easily on it. From what i have read anyway to write to NTFS in linux is still experimental. Maybe its changed but Fat32 has worked fine for me. Hope at least a lil help.

---

### Post by baldy1324 on 2006-08-05
check out this thread - [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009). it works like a charm.

---

### Post by dadude on 2006-08-05
jesus christ i'm a noob here. I hate long instructions in the terminal. :eek: 
I think that I will go fat 32. However if I recall isn't there a problem with 
writing like 2gb of files with fat. Maybe I'm wrong. 

Any Suggestions for the SCSI?

---

### Post by nix4me on 2006-08-05
Don;t use NTFS.  Just asking for trouble.  I know there is a new ntfs driver out but I just don't see the need for it.  Format that puppy ext3 and just share it.

The SCSI drives should be fine.

nix4me

---

### Post by misterE0 on 2006-08-06
if you are accessing your data remotely, you don't need to format as NTFS or fat32.  My current setup is a linux/win dual boot desktop and a linux file server, with my data drive partitioned as ext3.  Sharing the drive over samba, I can read/write to it without any trouble from either windows or linux.  In linux it's mounted in the media dir and operates as if it were a local drive, and in windows it's mounted as D: and also works as if it were a local drive.  All of this over gigabit ethernet, which is definately worth the few dollars to upgrade your hub/router.  So in short, unless your server has to be windows, why not just make the drive an ext3?  I haven't tried it myself, but i'm sure you can write to an ntfs drive on the network using samba from linux.

---

### Post by dadude on 2006-08-06
ext3? how would I go about formating the drive? doing so? The Drive is Westernd Digital My Book. Right Now an NTFS Drive. Also what is Samba? As I said I'm a total newb so if this sounds stupid i'm sorry? What about Fat 32? Is ext3 better?

---

### Post by misterE0 on 2006-08-08
you can format your drive using ext3 either during your linux install, or afterwards with mkfs.  Some googleing or reading the man page on that command should help.  Samba basically lets you network linux & windows computers together and allow read/write access as you like.  Fat32 is an old windows file system.  For large disks, it is not usually recommended.  Do a bit of reading on samba and I think you'll see that it's what you're looking for.

---

### Post by RedKrieg on 2006-08-08
a graphical partitioner/formatter is gparted.

```
sudo apt-get install gparted
```

It'll be in your System menu.

---

### Post by dadude on 2006-08-08
I've had some problems with gparted. Mostly with resizing the hard drive. I currently have got my dell inspiron dual booting with xp and somehow I was able to have gparted work. It was very weird. It said that there was an error and I could expirence severe file system damage on my xp partition. I rebooted and windows would not work. Then I installed ubuntu on the ubunutu partition. And windows works just fine. :) I have now Idea and don't care too much how it happened, It works and I'm happy.

---

