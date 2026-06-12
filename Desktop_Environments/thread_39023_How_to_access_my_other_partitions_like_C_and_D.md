---
title: "How to access my other partitions like C and D"
date: 2005-06-03
forum: Desktop Environments
---

### Post by xo310 on 2005-06-03
Hi. When I go to places and choose computer i see only file system cdrom and floppy. But i need also to use some files from windows partitions. how can i access them?
thank you

---

### Post by thagame on 2005-06-03
sudo gedit /etc/fstab

then at the bottom add a line like mine

/dev/hda1    /media/windows   vfat    umask=000         0         0

replace with your info. and remember to make a folder. 

eg. i made a folder /media/windows
      the drive is fat32 so i put vfat
      and its the first partition on my hd so /dev/hda1

---

### Post by xo310 on 2005-06-03
Hi, 
My partition is ntfc.  what should i change vfat with?
and what do you mean by "replace with your info"?
thank you
I am a total beginner so please barden my ignorance:-)

---

### Post by spencer on 2005-06-03
Try this link [here](http://www.ubuntuguide.org/#windows) . That should do it for you. I hope this helps.

-spencer

---

### Post by cutOff on 2005-06-03
Hi,

[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by spencer on 2005-06-03
You are correct. I just finished editing my post. Sorry about that.

-spencer

---

### Post by xo310 on 2005-06-03
thank you all

---

### Post by spencer on 2005-06-03
Sure thing. I hope it worked for you. 

-spencer

---

### Post by cutOff on 2005-06-03
[QUOTE=spencer]You are correct. I just finished editing my post. Sorry about that.

-spencer[/QUOTE]
No problem mate ;-)

---

