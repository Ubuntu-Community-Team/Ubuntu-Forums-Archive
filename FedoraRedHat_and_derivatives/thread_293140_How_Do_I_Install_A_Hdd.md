---
title: "How Do I Install A Hdd??????????"
date: 2006-11-04
forum: Fedora/RedHat and derivatives
---

### Post by lowlux2gmail.com on 2006-11-04
how do i install the HD so i can install Fedora 6 DVD?????????? its an IDE and its clean noting on it... the drive windows is using is on master cable now... the clean drive is unplugged.

slave? master? im getting a blank screen... no insert disk noting????](*,) :confused: 


i been at this for 2 days now! i done everything i could think of...

---

### Post by taurus on 2006-11-04
Okay, let me see if I get this right because I am not sure exactly what you just said!  You have two harddrives and have XP on the master drive, first drive.  You now want to install FC6 from a DVD and you've decided to disconnect the first harddrive so you can install it on the second drive!!!  If you want to install FC6 on the second drive, don't disconnect the first drive.  Hook it back as a master drive and the second as a slave drive.  Then tell FC6 installer to use the second drive, /dev/hdb.  This way, the installer will add an entry to boot your XP as well as your FC6...

Move this thread over to RedHat/Fedora Core section

---

### Post by lowlux2gmail.com on 2006-11-04
what is /dev ??

---

### Post by lowlux2gmail.com on 2006-11-04
WILL IT INSTALL ANYTHING ON THE WINDOWS DRIVE?????? i don't want Linux on my windows drive!

last time i installed Linux with windows dual boot..(SUSE pro 9.1) it wiped out windows and i was off line for 5 months. ](*,) 

what if i take the Linux drive out of the computer will windows still boot normal? could this harm windows in anyway?

---

### Post by Mihkal on 2006-11-06
When you get to the partitioner in the installer, choose custom partition (I'm not sure what it is exactly called in anaconda) 
Then choose to format the second drive for / ( / is the root file system where everything gets installed for any linux distro)
the second drive should be called hdb2. The partitioner will display the sizes of each hard drive, so you can check which one is the windows harddrive.
I hope this helps

---

