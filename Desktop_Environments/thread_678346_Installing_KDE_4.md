---
title: "Installing KDE 4"
date: 2008-01-25
forum: Desktop Environments
---

### Post by Kbeginner on 2008-01-25
I am not having any luck installing KDE 4 (I don't think).  I'd like to remove whatever I did install and start over.

I am a beginner and I am confused by the entry:  

> You&#8217;ll want to then append this line:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

After I 

> sudo vim /etc/apt/sources.list

I am not sure how to "append" the above line.  Do I have to enter ":" first?

Then it says once installed I can run from "login manager" which I assume means I have to restart, but when I did last time, I did not get the option of starting with KDE 4.

Please help.

Thx.

---

### Post by MasterJS on 2008-01-25
That line you have to add to your sources list. What you do is go to a Terminal and type "gksudo gedit /etc/apt/sources.list" and when you get into the file, scroll down till you get to a list of the same style (starting with deb) and add that line to the bottom of the file. Save it and exit. Then in the terminal type "sudo apt-get update" to update your sources and you should be able to download everything you need. Oh, and another thing, you don't need to restart. You just need to log out. You can do this by pressing CTRL+ALT+BACKSPACE and you will end up back at the login window.

---

### Post by Kbeginner on 2008-01-25
Ahhh, cheers.    Thank you.   Very helpful.  This has been quite the educational day.

---

