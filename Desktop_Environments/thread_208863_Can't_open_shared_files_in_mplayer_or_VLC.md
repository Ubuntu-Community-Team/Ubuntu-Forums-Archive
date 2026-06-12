---
title: "Can't open shared files in mplayer or VLC"
date: 2006-07-04
forum: Desktop Environments
---

### Post by OrangeGoblin on 2006-07-04
I have a shared folder set up on my XP machine, and when I try and open the videos in it using mplayer or VLC on Ubuntu, the applications open but they don't open the files. Using totem opens the files fine, but totem doesn't support a bunch of codecs and I'd much rather use mplayer or VLC. I think it is a samba issue as neither mplayer or VLC recognise the smb:// protocol. What can I do to fix this? Thanks.

---

### Post by simonn on 2006-07-04
I haven't tried this, but in theory if you mount the share (using mount or in /etc/fstab) then the share should become part of the file system. Mplayer et al should then be able to play the files.

---

### Post by Thund3rstruck on 2006-07-04
OrangeGoblin,

 I always store all my videos on a W2K3 server and view them remotely through mplayer (wmv, mpg, mov, etc, etc) on linux. Then again, all my smb shares are mounted automatically in /etc/fstab on boot. 

 Try creating a folder called videos 
```

mkdir -p /mnt/server/videos
``` and then mount the WinXP share 
```

mount -t smbfs -o username=MyWindowsUser,password=MyWinPasswd //ServerName/ShareName /mnt/server/videos 

```

Now try watching the video from the new mount point

---

### Post by OrangeGoblin on 2006-07-04
Cheers, that worked!

---

### Post by aleska on 2006-07-11
This is one of the threads I used to trouble shoot my problem.  I was trying to do something similar but with music, and not on an XP box, but a Buffalo Linkstation network storage device.  I'm getting weird error messages when trying to mount.
[My Post]("http://www.ubuntuforums.org/showthread.php?t=213824")
Any insights?
Thanks in advance!
-aleska

---

