---
title: "Diablo 2 &quot;play disc not detected&quot;"
date: 2006-01-12
forum: Gaming &amp; Leisure
---

### Post by Dark Damo on 2006-01-12
I managed to get Diablo 2 to install with Wine. But when ever i click the icon i get an error saying that it couldent detect the cdrom even when its in the drive spinning. And the auto play even comes up too!

Anyone have idea's?

Thanks from Damo :p

---

### Post by Imexius on 2006-01-12
use: sudo -s to go into root, from there just mount your you cd drives and copy and paste their contents into individual foldrs. Once thats done the install again and when it askfs for disk to just link it to the folder.

To mount your cdrom drive just go sudo mount /dev/hdc /media/cdrom
 -o umask=000

---

### Post by Dark Damo on 2006-01-12
Is there any easier way?

---

### Post by leech on 2006-01-13
Actually I think the reason for this is the copy protection.  Go to [www.megagames.com](www.megagames.com) to get the no-CD crack.

Leech

---

### Post by Dark Damo on 2006-01-13
Oh ok. Will i still be able to play online? All i need is to play it online and i am fine. I dont need to worry about single play ;)

I did a full install anyway so i dont have to worry about cutscene disc.

---

### Post by Iesos on 2006-01-18
You can do it without cracking it (i've heard). I hade a similar problem with starcraft this is the solution:

run:
 $ winecfg
Go to devices. You have probobly just c: and z: asigned to some of you mount points. Try the "Auto-detect" button. It still didn't work for me (but it should). I had to press "Add..." and then select a mount point, (i dont know if the will be some conflict if you choose one of the already chosen mount points, that where asigned when you pressed "Auto-detect".) I chose /cdrom/ . Then:
 $ mount /dev/hdc /cdrom/
 $ wine diablo2.exe
And then it should work, at least that should fix the cd-detection problem.
Good luck!

---

