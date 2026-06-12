---
title: "Ubuntu created folder acces in Win XP"
date: 2009-06-11
forum: General Help
---

### Post by xova02 on 2009-06-11
Hello,

First, I apologize if this is inappropriate question - I am not sure whether it is more Linux or more Windows issue.

Well, I have dual boot win WinXP and Ubuntu 9.04, Ubuntu came later. I renamed some folders on a NTFS external drive in Ubuntu and now I cannot acces them in XP. When I try to, I can hear only the well-known Win error sound and nothing more. Preferences show size of those folders - 0 bytes. Of course I can access them in Ubuntu.

I am new to Ubuntu, so I have no clue what to do about it and I have already gone through the forums searching for similar topic.

Thank you for help,

Xova

---

### Post by ActiveFrost on 2009-06-11
Terminal ( replace folder_path with one of your WinXP folders ) :
```
cd /folder_path
ls -l
```
Show us the output ;)

---

### Post by xova02 on 2009-06-13
Well, I cannot even do that. 

xova@xova-desktop:/media/MyBook$ ls -l
celkem 25
-rwxrwxrwx 1 root root  103 2009-05-18 14:38 autorun.inf
drwxrwxrwx 1 root root 4096 2009-06-06 14:19 $AVG8.VAULT$
drwxrwxrwx 1 root root 4096 2009-06-10 12:14 Data
-rwxrwxrwx 1 root root 4543 2009-06-05 14:01 menu.lst
drwxrwxrwx 1 root root    0 2009-03-30 14:48 $RECYCLE.BIN
drwxrwxrwx 1 root root    0 2009-05-19 17:13 Recycled
drwxrwxrwx 1 root root 4096 2009-05-19 17:15 RECYCLER
drwxrwxrwx 1 root root 4096 2009-03-22 16:22 System Volume Information
xova@xova-desktop:/media/MyBook$ cd /Data
bash: cd: /Data: No such file or directory
xova@xova-desktop:/media/MyBook$ cd /Recycled
bash: cd: /Recycled: No such file or directory
xova@xova-desktop:/media/MyBook$ 

I cannot get through the folder "Data" in Terminal, to reach the desired one, which cannot be accessed in WinXP.

---

### Post by blueridgedog on 2009-06-13
You typed: cd /Data and it should be cd /media/MyBook/Data or simply cd ./Data

---

### Post by xova02 on 2009-06-14
Oh, thanks for little Terminal tutorial. I really am new to Ubuntu... Well, problem resolved, I found out that Windows don't like it when folders contain ":" symbol in their names, which was the issue of those particular folders.

Anyway, thank you very much for your attention.

---

### Post by blueridgedog on 2009-06-14
> **xova02 said:**
> Oh, thanks for little Terminal tutorial. I really am new to Ubuntu... Well, problem resolved, I found out that Windows don't like it when folders contain ":" symbol in their names, which was the issue of those particular folders.

Anyway, thank you very much for your attention.

Don't give up!  The terminal is a mighty tool and you will master it.  Just like getting your head around "drive letters" you can get your head around "paths".  Anything that starts with / is assumed to start from the base or the root of the file system.  If you mean to refer to "here" then that is ./ which is "dot slash".

---

### Post by anjelicaboeh1 on 2011-01-14
> **xova02 said:**
> Hello,First, I apologize if this is inappropriate question - I am not sure whether it is more Linux or more Windows issue.Well, I have dual boot win WinXP and Ubuntu 9.04, Ubuntu came later. I renamed some folders on a NTFS external drive in Ubuntu and now I cannot acces them in XP. When I try to, I can hear only the well-[[COLOR=#000000]known[/COLOR]](http://www.redcov.net/small-business/small-business12.html) Win error sound and nothing more. Preferences show size of those folders - 0 bytes. Of course I can access them in Ubuntu.I am new to Ubuntu, so I have no clue what to do about it and I have already gone through the forums searching for similar topic.Thank you for help,XovaIt helps me out of the problem, Thanks for your explanation! It's comprehensive, I got more deep understanding about this part.

---

