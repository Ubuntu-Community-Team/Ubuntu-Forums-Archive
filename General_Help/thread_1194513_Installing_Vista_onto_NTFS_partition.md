---
title: "Installing Vista onto NTFS partition"
date: 2009-06-22
forum: General Help
---

### Post by jsoellner on 2009-06-22
Hi

I bought a Dell Inspiron 1525 that came with an OEM copy of Windows Vista.

I reformatted the entire hard disk and installed Ubuntu, after trying out various Linux distros.  Everything has been great and I am glad I made the switch to Linux, but I have one annoying problem, which hopefully somebody can help with...

I am currently studying for my CompTIA A+ and have some course material on CD.  The CD is basically full of videos (with meaningless filenames), that are launched by a program on the CD that shows a menu (.exe).  There is an autorun file on the CD so obviously it's meant to be viewed under Windows.

Tried running the .exe in WINE but that doesn't work.

I decided to reinstall Vista so I could view the CD properly, through the program on the CD.  I created a 40gb NTFS partition on my HDD and booted from the Windows Vista DVD.

I select the partition to install onto and get the error message "Windows is unable to find a system volume that meets its criteria for installation".

I have tried using the windows partition manager software on the Vista install CD to delete the NTFS partition I made with GParted and create & format a new one with no luck.

Any ideas?

---

### Post by Sef on 2009-06-22
1) You have to install Vista on the first primary parition.   

2) Can it be detected on another computer?   The disk could be bad is a possibility.

---

### Post by jsoellner on 2009-06-22
I will create a new NTFS partition as the primary partition tomorrow and try that.

For now, I'm hitting the hay, but I'll let you know tomorrow if it worked!

---

### Post by michy99 on 2009-06-22
Have you tried playing the videos in any linux players?

---

### Post by jsoellner on 2009-06-22
Yes I can do that, but there are lots of videos (about 40) with pretty random filenames, so I don't know which video is for which subject.

I am just trying to avoid having to guess which video is which, also the menu allows access to the study structure and mock exams.

I am also studying Network+ and Server+ which have the same type of CDs...

---

### Post by jsoellner on 2009-06-28
Solved. I had to do a backup, reformat my entire hard disk before windows would install, then shrink the windows partition (which wasn't easy because windows puts system files in dumb places) and reinstall Ubuntu.

Dicking about with windows took more time than reinstalling linux, installing all my software again and restoring my backup.

But at least I can study now, so no more putting it off.

---

