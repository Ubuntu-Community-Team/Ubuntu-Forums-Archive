---
title: "Ubuntu Won't Start - Conflict with MySQL?"
date: 2008-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mr.alA on 2008-07-20
When I start Ubuntu 8.0.4 on my Dell, it lets me get to the login screen, but once I enter my username and password and login, it instantly freezes, and responds to no keystrokes.  

I hit the power button on the tower, and the GUI disappears and goes to plain black and white text terminal, where it shows a bunch of items which I assume are a list of applications and/or processes starting.  

For example, on the list there is: 
**Starting Common Unix Printing System
and then a box to the right says [ OK ]

BUT

Another one of these says

Starting MySQL database server mysqld
and the box to the right says [FAIL]

Could this be the cause of the freezing?  If so, what can I do to alleviate this problem?

---

### Post by Potatoj316 on 2008-07-21
I have a few questions.  Does your computer eventually let you log in to the GUI?  Do you use MySQL?  Does pressing crtl+alt+F1 bring you to a termilal login screen?

---

### Post by mr.alA on 2008-07-22
It gets only to the GUI login screen, and freezes 4-6 seconds after I enter my username and password.  The login screen disappears, but it is replaced with an empty screen, the one it displays before it loads your background and icons. 

Yes, my computer is using MySQL. And I will try the key combination you're talking about next time I can.  Thanks for the advice so far!

---

### Post by stevoo on 2008-07-23
Yes try and get into safe mode
by pressing ctrl+alt+f1
there login
and type sudo -s to login as super user

But, i would like more info to determine what the problem is with mysql.

You could try removing it and reinstalling it.

---

### Post by mr.alA on 2008-07-23
Will do.  Thanks for the advice!

---

### Post by mr.alA on 2008-07-26
Okay, so I went into safe mode using atrl-alt-f1.  When I did this, the text appeared to login to the terminal, but it was HUGE.  Is there any way I can fix the text size?  The text is so big I cannot see what commands I am putting in, or the responses, etc.

---

