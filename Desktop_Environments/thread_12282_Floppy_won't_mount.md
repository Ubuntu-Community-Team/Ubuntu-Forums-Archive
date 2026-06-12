---
title: "Floppy won't mount"
date: 2005-01-23
forum: Desktop Environments
---

### Post by buttonpusher on 2005-01-23
I have some word documents on a 3.5 disk that I need to edit (my XP box is down) and my problem is that when I try to assess the files it indicates that it is not able to determine the format of the disk/floppy and the mount fails.  I'm using from the computer drop down menu (Files) and double clicking on the floppy icon when it is displayed.  After that I get the error message.  I want to access the files on there using the open source word processer, but with it not able to mount the floppy I'm in a major bind.  Does any one know of a fix or work around that I could use??

Thanks to all in advance,

Buttonpusher ](*,)

---

### Post by m_gasior on 2005-01-24
sudo gedit /etc/fstab

change:
/dev/fd0  /media/floppy0 auto ...
to
/dev/fd0  /media/floppy0 vfat,ext2 ....

---

### Post by towner on 2005-01-25
hi Button pusher,

I had a similar problem and posted my solution in the installation help forum on 24 / 01 / 05. 
Towner

---

### Post by buttonpusher on 2005-01-26
m_gasior &  towner 

 I followed the instructions and was able to finally mount my floppy drive and save a document to it.   :) 

Thanks for the assistance as I would still be scratching my head on why it didn't work.

Buttonpusher

---

