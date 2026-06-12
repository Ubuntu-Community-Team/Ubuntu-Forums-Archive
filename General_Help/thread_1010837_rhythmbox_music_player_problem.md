---
title: "rhythmbox music player problem"
date: 2008-12-14
forum: General Help
---

### Post by abhilashm86 on 2008-12-14
when i start rhythmbox music player,before it would have lost all songs and data,again i need to go to FILE->add folder,then start playing songs,every time it will erase songs and data,why is this happening,how to solve it?please help.......

---

### Post by Arup on 2008-12-14
If you have your music in separate partition, you need to automount it on boot, otherwise Rythmbox looses the music.

---

### Post by acreech on 2008-12-15
> **Arup said:**
> If you have your music in separate partition, you need to automount it on boot, otherwise Rythmbox looses the music.

How do you "automount" I have my music folder on a second internal hard drive. 

thanks

---

### Post by tuxxy on 2008-12-15
Add the partition to your /etc/fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

