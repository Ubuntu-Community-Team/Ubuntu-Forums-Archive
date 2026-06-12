---
title: "Pegasus and Wine"
date: 2008-08-25
forum: Desktop Environments
---

### Post by oygle on 2008-08-25
This relates to [this archive thread]("http://ubuntuforums.org/showthread.php?t=168206&highlight=pegasus") - the probable reason you are getting the msg "User cannot be found" is because the usernames in Pegasus relate to folder names for mail boxes and newmail.

Just checkout the file pmail.cfg , plus you will probably have to modify the file pmail.ini , as it contains folder names also.

---

### Post by oygle on 2008-09-04
WINE by default has "drive_c" setup as a folder to contain other folders like:

Program Files
windows

The file that is most likely causing this meesage is called pmail.cfg , I did a cat of it and got:

$ cat PMAIL.CFG
D:\PMAIL\NEWMAIL\~8D:\PMAIL\MAIL\~8

(tilde 8 is just the username)

so whilst WINE has dive "C" setup as /.wine/drive_c/ , when Pegasus runs, it is looking for Drive D for starters.

There is a program to modify the contents of PMAIL.CFG, it is called 'pconfig.exe'

Tried running it, and got an error message ..

$ wine pconfig.exe
winevdm: unable to exec 'C:\Program Files\PMAIL\pconfig.exe': DOS memory range unavailable

There must be some sort of hex editor on Ubuntu, to modify those 2 path names in the file PMAIL.CFG

Also, I've been caught out several times with the caseing of files and folders, as Win didn't care, but Linux does.

HTH

---

### Post by lwb4007d on 2008-09-04
[size=2]wow,nice yeeeeehhhhhhhhhhhaaaaaaaaaaa[/size]------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU30U016.jpg[/img]our wow power leveling site:cheap [wow power leveling](http://www.toppowerlevel.net).buy [wow power leveling](http://www.yoyo-power-leveling.com).[wow power leveling](http://www.swow-power-leveling.com).cheap [wow power leveling](http://www.wow-powerleveler.com).[wow power leveling](http://www.wow-power-leveling1.com)

---

### Post by oygle on 2008-09-05
Ran pconfig.exe on a Win box to modify the contents of pmail.cfg , so that the paths for mail and newmail reflected the WINE path on Ubuntu. Then used that modified pmail.cfg and the "user not found" message no longer appears.

Pegasus opens okay, can view folders and emails okay, however when I tried a test send, Pegasus 'exits', it's like it closes down ?

I _think_ this is a common problem (bug).

---

