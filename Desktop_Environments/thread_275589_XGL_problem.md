---
title: "XGL problem"
date: 2006-10-11
forum: Desktop Environments
---

### Post by SexyPastry on 2006-10-11
XGL and Beryl seemed to install fine until i needed to choose my session it says it cant find the startxgl.sh when i created it and all then it says that the xsession cant find it or start it any ideas?

---

### Post by WPAStrangla on 2006-10-11
Log into Gnome click "Alt+F2" and type in "Beryl-Manager" see if that works

---

### Post by SexyPastry on 2006-10-11
How do u click "alt + F2" when i type it doesnt do anything..

Any other ideas?

---

### Post by WPAStrangla on 2006-10-11
click Alt+F2 on your keyboard and a Window should pop up, Type Beryl-Manager in that. Also which guide did you follow?

---

### Post by SexyPastry on 2006-10-11
Nothing pops up when i hit "Alt + F2" in regular session or GNOME session and i used this to install it 


[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

---

### Post by krisbowen on 2006-10-11
maybe look at your executable code:

$ sudo chmod +x /usr/bin/startxgl.sh

I have seen different ones for this line particularly in the Racer11 howto on the Beryl forum

***EDIT: on the Edgy thread it suggests this instead:
Code:

sudo chmod 755 /usr/bin/startxgl.sh

---

### Post by SexyPastry on 2006-10-11
Thx for the help guys got the log into xgl session.

Now it wont stay logged into the xgl session and goes back to the login screen where u login and choose session... Also when i had the time period of trying to change something nothing happened  any ideas?

---

### Post by krisbowen on 2006-10-11
When you log into a gnome session are you able to see the red jewel in the upper right hand corner?

If so have you tried to use beryl to start the session from gnome??

What graphics card are you using??

What comands are issued at startup??

---

