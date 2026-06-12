---
title: "partition errors"
date: 2007-08-29
forum: Dell  Ubuntu Support
---

### Post by bmackenty on 2007-08-29
Hello Friendly Ubuntu folks! 

I am trying to install (dual-boot) Ubuntu 7.04 on my Windows XP pro machine (Intel Pentium 4 3.0ghz with 2GB ram) .

However, I am unable to partition my NTFS drive! 

My current disk partition map looks like this: 

/dev/sda1  |   fat16 | used: 7.87MB |  free: 62.70MB
/dev/sda2  |  NTFS   | used: 58.89GB | free: 15.53GB | Boot 

I have used the <a href="http://gparted.sourceforge.net/livecd.php">gparted live CD</a> and I have <a href="https://help.ubuntu.com/community/WindowsDualBoot">read this helpful entry and tried using the system recovery CD</a>.  The partition error message says that the NTFS drive cannot be shrunk...which I don't understand. 

Any help would be warmly received!

Thanks!

---

### Post by jongkind on 2007-08-29
The space left to add an extra partition is rather small (15.53 GB). That may partly contribute to this problem. What you can try to do is:

1-defragment the XP partition and try to create a new partition again.
2- if that is not successful you can try to use the Gparted LiveCD to create the new partition. That can be downloaded from: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

### Post by rsambuca on 2007-08-29
Personally, I wouldn't shrink that drive unless you remove some files first.  Windows won't work very well unless it has some free room on the drive.  The reason it won't let you shrink it is because of the unmovable files in Windows.

---

