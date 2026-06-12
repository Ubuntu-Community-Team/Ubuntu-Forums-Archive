---
title: "Ut2003 install trouble"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by howitzer99 on 2008-05-13
OK i am trying to install UT2003 when i go to run the linux_installer i get this error message .. i am new to linux and Ubuntu Hardy in general so can someone plz help me.. this is the err i get when i run the installer 

dave@dave-desktop:~$ sh linux_installer.sh
Copying to a temporary location...
Verifying archive integrity...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 646206283 is different from 3043856338
dave@dave-desktop:~$ 

i have tried to run it with sudo in front of the sh command as well. :confused:

i am thinking that my installer is damaged in some way..where the checksums err is coming up.

---

### Post by 1337 on 2008-05-13
Package seams to be corrupt, try redownloading it maybe from a different source.

Regards

---

### Post by howitzer99 on 2008-05-13
ok got it working .. the installer that is .. i have not started the game yet . but all should be fine now.. i found on another post theis command .. and it worked .. the error is from and older game looking for the older lib files i guess.. anyways this worked for me.. 

sudo _POSIX2_VERSION=199209 linux32 sh /media/cdrom/linux_installer.sh

i just changed the install path and symb. link paths to my home folders.. using the drop down arrows..


:popcorn:

Also i just figured out that when the installer asked for  the play disc that is cd 1 .. when asked for cd 1 thats cd2 and so forth.. :lol:

---

### Post by PaulReaver on 2009-04-23
Click here. Follow this. [http://ubuntuforums.org/showthread.php?t=1129279&highlight=ut2003]("http://ubuntuforums.org/showthread.php?t=1129279&highlight=ut2003"):P

---

