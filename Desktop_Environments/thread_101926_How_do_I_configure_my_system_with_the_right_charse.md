---
title: "How do I configure my system with the right charset"
date: 2005-12-10
forum: Desktop Environments
---

### Post by otey on 2005-12-10
I have been messing around a bit, and i think ive ruined something.. I want to set my ubuntu up with danish charsets. How do i do it?

fx. When i use gedit to make an html file, the letters **&#230; &#248;** and **&#229;** are replaced by some very odd signs. **&#230;** is **&#195;&#166;** - **&#248;** is **&#195;&#184;** and **&#229;** is **&#195;&#165;**.. I have some html files _saved before the messup_ and they work fine.. 

No problems in my homefolder.. i have some dirs named with the letters. They are displayed fine.. but on my *vfat* harddisk the names **Bj&#246;rk** and **Bj&#248;rn Svin** is displayed like **Bj?rk (invalid encoding)** and **Bj?rn Svin (invalid encoding)**.

When my brother *(Windows XP)* accesses my ftp.. Caf&#233; is displayed like Caf[crap like first example]

What do i do?
And what should my fstab line be?
Now it's: /dev/hdd5       /media/hdd5     vfat    defaults,umask=000			0       0

---

### Post by otey on 2005-12-12
Okay.. now i've realized that I am not going to get an answer.. But can I get a hug then.. I feel so alone.. :cry:

---

### Post by ape on 2005-12-13
Not sure if you got your hug or not, but for the charset issues, two things to try:

1. Run `sudo dpkg-reconfigure locales` and configure those locales that you want  enabled on the machine.  After doing this, ensure that you set the required LC_* and LANG variables to the charset you want (in your .profile or .cshrc, whatever the case may be). (Probably to something like this "LC_ALL=da_DK.UTF-8") <not sure if that is the Danish language assignment, sorry...<G>>

2. When you get to the GDM login screen, ensure that you are choosing the language you want to be using.

Hope this helps...


EDIT:  Just found this forum [link]("http://www.ubuntuforums.org/showthread.php?t=102778") that might help.

---

### Post by otey on 2005-12-13
It solved the problem with the dir- and filenames. fumbled around with the locals like you said, but the thing with the letters &#230; &#248; and &#229;, is still buggin'. 

I could not find the .profile or .cshrc file.. where is it? 

btw.. I'm not interestet in the dansih translation. I just want gedit to save my html-files without me having to change it to stuff like &aelig; and &oslash; notepad works that way.. and i miss that :sad:

---

### Post by otey on 2005-12-16
[QUOTE=otey]When i use gedit to make an html file, the letters **æ ø** and **å** are replaced by some very odd signs. **æ** is **Ã¦** - **ø** is **Ã¸** and **å** is **Ã¥**.. [/QUOTE]
I feel so dumb.. I found out that gedit let me choose the charset for the file, when it is saved.. i just have to choose iso-8859-15 instead of utf8.. 

:D 

well sorry for bothering and thanks to ape for help

---

