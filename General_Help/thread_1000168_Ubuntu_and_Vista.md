---
title: "Ubuntu and Vista"
date: 2008-12-02
forum: General Help
---

### Post by skulldragon3200 on 2008-12-02
I have both Vista and Ubuntu installed on the same laptop. What I would like to do if use my current World of Warcraft installation in Ubuntu. I have installed Wine and from the Ubuntu help files, I am at the point where it says that I need to copy the files over. The problem is that I do not know where to copy the files, as I can not see the Ubuntu files from Windows and vice versa.

Any suggestions on how to move it over?

(I am new to Ubuntu and have been reading the documentation and everything and I am still not understanding what I must do)

Thanks guys. :D

---

### Post by TeXtonyx on 2008-12-02
I don't play it, but I've seen several guides on how to install it.
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by skulldragon3200 on 2008-12-02
Yes, I have been using that guide and have done everything is has said. But, I guess my main question is referring to this part of that guide:

Alternative 1 (Copy from Windows):

You can also just install WoW in Windows and then copy the entire World of Warcraft folder over from your Windows installation. 

I already have it installed in my Windows. I am not sure where to copy the files so that I can see them in Ubuntu.

---

### Post by zwygart on 2008-12-02
In Linux to access drives/partitions, you have to mount them.

First type```
sudo fdisk -l
```in a terminal. This will display your partitions.
Find out wick is your windows partition (it should be in NTFS)
Remember the partition in form /dev/sdXY. X is a letter and Y a number (may be not there).
Then you have to mount the partition.
For information check at [http://users.bigpond.net.au/hermanzone/p10.htm]("http://users.bigpond.net.au/hermanzone/p10.htm")
Then run these commands
```
sudo mkdir /media/win
sudo mount /dev/sdXY /media/win
```
replace XY with the number you found (usually /dev/sda1)
This should create a icon on the desktop from where you can access your windows partition. Ifnot you can go trough My Computer, file system, media, win, and so on.
If it not works post the output of fdisk -l (To copy press CTRL + SHIFT + C) and the partition where your files are.

---

