---
title: "modifying drop shadows"
date: 2012-07-20
forum: Desktop Environments
---

### Post by doyleman on 2012-07-20
Hello all. I've been trying to tinker with Ubuntu 12.04's drop shadow in the theme. I quickly found out that Compiz can only go to 18 on radius, and to give it more, you should go and modify the <shadow> xml tags in it's theme folder. I've pumped the number up to 48 (actually, i've tried 0, 12, 24, 36, and 48); all of which really give no change. It actually looks like Compiz still controls the shadows 100%, but I can't get it higher than 18. Anyone have this issue?

---

### Post by doyleman on 2012-07-21
bump

---

### Post by doyleman on 2012-07-22
i'll bump again. no one has any thoughts / success...?

---

### Post by tahseen on 2012-07-22
Same here. I have been trying from a long time. I don't know why the Compiz developers are not reply to this question

I even wrote to the mail list.

Hope they have not hard coded this stuff. This is one question no one is able to revert to ever since Ubuntu 12.04 has been released.

---

### Post by doyleman on 2012-08-02
Well, I've read articles that modifying the xml file in the theme folder would work, but I seriously can't seem to tell any changes in 12.04. hopefully not. can anyone confirm/deny?

---

### Post by tahseen on 2012-08-02
I have done some modifications by editing metacity xml file and it does work.

But dropshadow doesn't. It seems dropshadows are controlled by Compiz only


> **doyleman said:**
> Well, I've read articles that modifying the xml file in the theme folder would work, but I seriously can't seem to tell any changes in 12.04. hopefully not. can anyone confirm/deny?

---

### Post by javagreen on 2012-08-06
Which file exactly are you editing? I'm looking to achieve the same result and knowing which file to edit is a good start ;)

---

### Post by tahseen on 2012-08-06
Go inside /usr/share/themes
There are theme folders. Every theme folder has a metacity-1 folder.

Inside that folder there is a metacity-theme.xml file.

You can edit that with sudo vi 

Once edited, logout and then login for the effect to take place or even compiz --replace though logout and login is better




> **javagreen said:**
> Which file exactly are you editing? I'm looking to achieve the same result and knowing which file to edit is a good start ;)

---

### Post by javagreen on 2012-08-07
The theme I want to edit has a metacity-theme-1.html and metacity-theme-3.xml :o

---

### Post by tahseen on 2012-08-07
I have serious doubts that there is anything called metacity-theme.html



> **javagreen said:**
> The theme I want to edit has a metacity-theme-1.html and metacity-theme-3.xml :o

---

### Post by javagreen on 2012-08-07
> **tahseen said:**
> I have serious doubts that there is anything called metacity-theme.html

Bugger, typed too fast and didn't even realize it. Yep, it's not html - it's xml, both the files. 

:guitar:

I've looked at both xml files, they mostly contain stuff about window frame and buttons. I've attached both the xml files in a zip, can you please take a look and advice on where do I need to change to manipulate the drop shadows :)

---

