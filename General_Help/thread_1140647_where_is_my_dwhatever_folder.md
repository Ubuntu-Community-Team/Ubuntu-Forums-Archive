---
title: "where is my d:\whatever folder?"
date: 2009-04-27
forum: General Help
---

### Post by LLLJJ on 2009-04-27
Hi! 

Thank you in advance for helping a newb out =)

I installed ubuntu via the windows installer thingy (d:\ubuntu). I can find my c: drive just fine, (i just mount it) but where is the rest of my d: drive? For example, I want to listen to the music I (in windows) have on d:\music, but I cant find d:\music.

---

### Post by mb_webguy on 2009-04-27
My guess is that the partition that Windows calls "D" isn't being mounted in Ubuntu.  I'm not familiar with Wubi, but if this were a normal installation, I'd say to open the terminal and use the command "sudo fdisk -l" to identify all of your drives and partitions, and "mount" to show all of the currently mounted partitions.   If the partition isn't currently being mounted, you can use the following commands to mount it for the current session.```
sudo mkdir */some/new/directory*
sudo mount /dev/*xxxn /some/new/directory*
```
To mount it permanently, you'd have to add an entry to the [/etc/fstab]("https://help.ubuntu.com/community/Fstab") file.

But as I said, I'm not familiar with Wubi installations, so it may be a completely different issue.

---

### Post by LLLJJ on 2009-04-27
Thank you for your reply. 

I found the solution for anyone interested. Apparently everything already on the drive where you place the ubuntu istalation can be found in \host

---

### Post by lvleph on 2009-04-27
Well /host not \host.

---

