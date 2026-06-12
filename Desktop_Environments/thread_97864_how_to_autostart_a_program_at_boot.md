---
title: "how to autostart a program at boot???"
date: 2005-12-01
forum: Desktop Environments
---

### Post by gold4tune on 2005-12-01
Is somebody can tell me what I should do to make a program autostart when my computer boot.  i tried to put a link of the applicatoin in .kde/autostart and in /etc/rc2.d, but nothing worked.

thx!!!

---

### Post by aysiu on 2005-12-01
Any reason you need the program to start at boot up and not once you log in?

---

### Post by gold4tune on 2005-12-01
I want sunbird to start automaticaly.  I want my alarm when i wake up in the morning...  I often forget to start it and, sometime, i don't see important things i have to do for the day.

I tried kdocker, but it doesn't work.

---

### Post by sinbad782 on 2005-12-01
How about putting an entry in the ~/.xinitrc file?

---

### Post by aysiu on 2005-12-01
So, let me ask again... any reason you need Sunbird started at boot time as opposed to first thing after you log in?

P.S. Have you checked this out?
[http://www.kde.org/areas/sysadmin/startup.php](http://www.kde.org/areas/sysadmin/startup.php)

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=gold4tune]Is somebody can tell me what I should do to make a program autostart when my computer boot.  i tried to put a link of the applicatoin in .kde/autostart and in /etc/rc2.d, but nothing worked.

thx!!![/QUOTE]
Maybe you could check out BUM (boot up manager). [http://ubuntuforums.org/forumdisplay.php?f=75]("http://ubuntuforums.org/forumdisplay.php?f=75")

---

### Post by gold4tune on 2005-12-02
thx everybody, 
I will try all your ideas and give you some news soon as possible!

---

### Post by gold4tune on 2005-12-03
> 
How about putting an entry in the ~/.xinitrc file?


How i do it...  I just add the path to the application in the file???

---

### Post by gold4tune on 2005-12-10
Ok, i find a way to do it...  For everyvody, if you want to start an application at the startup of your computer (on kde), jus put a link to it into /usr/share/autostart/

I tried it with sunbird and everything worked.

---

### Post by Sokraates on 2005-12-11
For clarity's sake:

Your solution will start an app after login, **not** at bootime or (in other words) systemstart. It's the difference aysiu asked you about before.

Usually you will want apps to start at login, that is when you see you KDE desktop. If you want to start anything right after the machine **boots**, it usually means startup before KDE is even initianlized. E.g. KDM is started at boottime. Otherwise you wouldn't have a graphical login .

---

### Post by gold4tune on 2005-12-11
oky thx,
I think i haven't use the good words to explain my'self...  Thats right i juste wanted the application to start when i log...  I see the difference now!!!  
Sorry for this little mistake.:rolleyes:

---

### Post by rafciu123 on 2007-02-18
Hi All,

I wanted to start on log in Skype so I did:
sudo cp /usr/bin/skype /usr/share/autostart
and it doesn't work for me.

I see skype under /usr/share/autostart and I can even launch it from there by double clicking but it doesn't autostart when I log in. I tried rebooting my machine and still doesn't work.

Please advice.

---

### Post by yathosho on 2007-10-10
follow these steps:

1, go to the *System* in the Ubuntu menu
2. choose *Sessions* from the Preferences menu
3. add a startup program (Skype should be in  */usr/bin/*)

---

### Post by gregfulkerson on 2007-11-30
thanks for the tip. I added a link to the /usr/share/autostart folder and it worked for me. 

by the way, I wanted to autostart "Glipper" which is a very handy clipboard utility that I recommend.

---

