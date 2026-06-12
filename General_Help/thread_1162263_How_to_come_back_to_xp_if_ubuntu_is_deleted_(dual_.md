---
title: "How to come back to xp if ubuntu is deleted (dual boot case)"
date: 2009-05-17
forum: General Help
---

### Post by s3nsiu on 2009-05-17
Hi to all. I came back to windows today not because i didnt like em...i know everything in life is not easy and....the easy path smtimes costs more and is not the ideal. But anyway due to a major crash i had on my ubuntu 8.04 i had to leave them for the moment and come back to the known paths...I tried to install to update my ati driver but eventually i ended see a totally white screen after the login!just i like a flashbang on counter strike for those of u who play or used to play the game.
Now i had an older experience with ubuntu and due to this i knew the most easy way to uninstall em without destroying ur other OS if in dual boot Xp-ubuntu
The algorithm is..
1. The first move is to login to xp and use ur favourite partition manager (acronis , partition magic etc). The ubuntu partition is still untouched to ur disk
2. Make sure u have a spare cd of xp smwhere....Any cd of xp would be usefull evev not the one u did the installation as long its the same xp type (pro, home etc)
3.If 2. is ok then delete the ubuntu partition and its swap file
4. Now if u restart....Dont be scared when u see the frightening black screen with the message
''NTLDR is missing"
NTLDR is the default win bootloader which was deleted from the first time u installed ubuntu and replaced by GRUB bootloader. Using the partition manager u deleted GRUB so now there is no bootloader in ur system to search for operating system....so
5. Insert the xp installation cd....Boot from cd.Wait for all the files to load. When is asks u what to do....Dont make a new installation!!!!!of course
6.Use repair mode (press R). Black screen appears. It will ask u what disc to repair. Press 1 and then enter to target ''C" disc. To all questions ''if u are sure'' press "y" and enter. The procedure is more simple than u think..I am just totally analytic
When end to command prompt
run commands
/fixboot
/fixmbr
Then type ''exit'' without the quotes to restart
Xp will load normally then.

I promise my self i ll come back to ubuntu soon...I liked this strange but new (at least to me!) world
Hope someone finds my topic useful. Bye

---

