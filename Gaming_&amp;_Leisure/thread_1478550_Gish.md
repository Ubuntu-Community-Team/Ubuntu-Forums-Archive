---
title: "Gish"
date: 2010-05-09
forum: Gaming &amp; Leisure
---

### Post by duckleet on 2010-05-09
ok I am new to ubuntu and I dont know how to get gish install and runing i have the tar file can someone help every one i ask just ends up being a jerk. please help me.
please make it a easy so a kid could do it

---

### Post by Bonster on 2010-05-09
1)Right click on tar.gz file and click on 'extract here'
2)Look for a file called 'gish' or 'gish64' depends on your OS is 32bit or 64bit
3)Right click on that file and choose 'Properties'
4)Click on 'Permissions' tab
5)Checkmark on the 'Allow Executing'
6)Close
7)Now Double-click on the file and it will run the game

---

### Post by duckleet on 2010-05-09
it does not what to run did every thing you said and it does nothing

---

### Post by hikaricore on 2010-05-09
Run it from a terminal window instead.  Post error output here.

---

### Post by duckleet on 2010-05-10
This is the error in terminal I get when I try to load it.


:(
```
./gish: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory
```

---

### Post by hikaricore on 2010-05-10
Install libopenal, I believe this was covered in one of the other 3 threads involving the humble indie bundle.
Easy fix if that's all there is to it.

---

### Post by duckleet on 2010-05-13
got it working and thank you

---

### Post by e-Gee on 2010-05-15
How to create louncher for gish ?

---

### Post by Perfect Storm on 2010-05-15
> **e-Gee said:**
> How to create louncher for gish ?

```
sh -c "cd <distionation> && ./<binary>"
```

---

### Post by Tethtibis on 2010-10-24
Ok, Set file to executable, installed all dependencies, running ( sudo sh -c "cd ~/Games/Humble\ Bundle/gish153/ && ./gish"
) from the terminal, even tried setting the executable to open with the "autorun prompt". double clicking does nothing, and running from terminal produces the error:

```
./gish: 1: Syntax error: Unterminated quoted string
```

at a complete loss at this point. Can anyone help? Thanks.

**_EDIT:_** Please disregard, i did more research, to find out that the executable I had downloaded was the 64 bit version back at the first part of the "Humble Bundle". it wasn't marked as 32 or 64 bit.

Downloading the latest version fixed the issue, because the tarball now included a clearly defined 32 and 64 bit version of the game.

Using the 32 bit binary fixed the issue, and it's working fine now. :O)

---

### Post by Perfect Storm on 2010-10-24
Why are you running and previous version of Gish? Get the latest here: [http://www.chroniclogic.com/gish.htm](http://www.chroniclogic.com/gish.htm)
Secondly, don't run it with sudo - only run sudo when you need to make changes to the system.

---

