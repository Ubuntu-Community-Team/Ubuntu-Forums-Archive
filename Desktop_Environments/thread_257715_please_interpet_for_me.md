---
title: "please interpet for me"
date: 2006-09-14
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-14
can some one please help me understand this-  winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Link points to "/tmp/ksocket-dougie"
can't create mcop directory

---

### Post by aysiu on 2006-09-14
Found [this solution](http://www.ubuntuforums.org/showthread.php?p=1154801#post1154801) in a Google search for your error. Does that help?

---

### Post by DougieFresh4U on 2006-09-15
/usr/lib/wine$ sudo mv winearts.drv.so winearts.drv.so.whatevermv: cannot stat `winearts.drv.so': No such file or directory

---

### Post by aysiu on 2006-09-15
I don't know, even the [other search result](http://ubuntuforums.org/showthread.php?p=1179227#post1179227) for your error had the same solution, and it worked for that person.

Can you post the output of these two commands (the first one may take a few minutes to execute)? ```
sudo updatedb
locate winearts
```

---

### Post by DougieFresh4U on 2006-09-15
dougie@ubuntu:~$ sudo updatedb
Password:
dougie@ubuntu:~$ locate winearts
/usr/lib/wine/winearts.drv.so.whatever
dougie@ubuntu:~$
this is all I got

---

### Post by aysiu on 2006-09-15
So it looks like it worked...? You managed to rename the *winearts.drv.so* file to *winearts.drv.so.whatever*.

Didn't solve your problem?

---

### Post by DougieFresh4U on 2006-09-15
I still don't understand what else I need to do now to run the game I want. I downloaded and it's on desktop but won't open, please guide me through, oh and thanks for your sincere help, as you have hekped me in the past (aysiu)!!

---

### Post by aysiu on 2006-09-15
Games are a bit outside of my realm of knowledge (I don't game!)

Maybe someone else can step in and help at this point...?

---

### Post by peabody on 2006-09-15
> **DougieFresh4U said:**
> I still don't understand what else I need to do now to run the game I want. I downloaded and it's on desktop but won't open, please guide me through, oh and thanks for your sincere help, as you have hekped me in the past (aysiu)!!

The name of the particular game you're trying to run would be useful information.

---

### Post by DougieFresh4U on 2006-09-15
I am trying to install "MahjongMedley" from Game House games. I have it on my winxp machine.Please do not suggest dual boot as I do not want windows onthis machine but I do enjoy some of the simple as they do not require alot extras (so I Thought) Can any help?

---

### Post by peabody on 2006-09-15
[http://appdb.winehq.org/search.php?sSearchQuery=Mahjong](http://appdb.winehq.org/search.php?sSearchQuery=Mahjong)

I don't see MahjongMedley on the list, however you may be able to get some help and even contribute to the wine project if you get in touch with the wine guys.

Is this mahjong game simple or does it have lots of fancy graphics?  Does it require 3d acceleration?  If so I believe you have to launch wine with the -opengl command line option.

---

### Post by DougieFresh4U on 2006-09-15
the game is very simple. but now when I click on the desktop icon for the game it says it may be corrupted, I don't know what to do.

---

