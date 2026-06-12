---
title: "Problem with installing AVG in my laptop"
date: 2009-06-21
forum: General Help
---

### Post by asamay81 on 2009-06-21
I was trying to install AVG anti-virus in my laptop using this helpline

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

Problem is that AVG appeared in Applications >> System Tools but without any icon. When I clicked on AVG Anti-Virus, this error window opened

[IMG]http://img134.imageshack.us/img134/18/screenshoterror.png[/IMG]

When I was trying to create the luncher using 

sudo rm -r /usr/share/applications/avggui.desktop

terminal gave me this output

rm: cannot remove `/usr/share/applications/avggui.desktop': No such file or directory

So, finally I could not install AVG in my system.

Need your help to fix this problem

Thanks

---

### Post by michy99 on 2009-06-21
1. The thread you linked to is out of date.

2. The current version of AVG free (8.5) has no gui, it is command line only.

3. I have never cared for AVG on linux. You might be better off trying a different anti-virus. (Actually, unless you are passing on files to Windows users, you don't really need one.)

---

### Post by asamay81 on 2009-06-21
thanks a lot for your reply. i downloaded the newest version of avg. actually my laptop is so loving to me, i try to take every care for it. in windows even i do not insert any external storage drive here. i do it buu ubuntu only. :)  so, no need any antivirus in linux for me :) now please tell me how can i uninstall the installed AVG 8.5....

---

### Post by michy99 on 2009-06-21
What method did you use to install? Was it a .deb file?

---

### Post by Chemical Imbalance on 2009-06-21
You really don't need antivirus unless you are scanning your windows partition with it.

Please read the stickies on the front page.  [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by asamay81 on 2009-06-21
the .deb file i installed using 
sudo dpkg -i <file name.deb>

yah i understood that i no need an anti-virus in  ubuntu...it itself is an antivirus :lol:

---

### Post by michy99 on 2009-06-21
```
sudo dpkg -r <file name.deb>
```

---

### Post by asamay81 on 2009-06-21
i am veru foolish that i know :( what i have done is, i deleted the .deb file from the desktop where i have downloaded the same. the program is installed in /opt folder. so what shoul i do to remove it now?

---

### Post by TransitMan on 2009-06-21
Open Synaptic, do a search for AVG, click on it and then REMOVE completely.
Click Apply at the top and it should take care of it.

---

### Post by asamay81 on 2009-06-21
:yahoo: i have completely removed avg. 

thanks a lot for your replies. 

this thread may be closed now..my problem has been solved :)

---

