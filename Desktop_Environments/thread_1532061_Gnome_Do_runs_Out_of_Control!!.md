---
title: "Gnome Do runs Out of Control!!"
date: 2010-07-15
forum: Desktop Environments
---

### Post by kid1000002000 on 2010-07-15
I have an intermittent problem with *gnome do* that I do not know how to fix.  I will start to notice that my system is running much slower than usual, and so enter the system monitor and check my processes.  Lo and behold, gnome-do is running at like 146 % CPU, and I have to end the process.  After I quit it and restart the application, it runs just fine for a while before the next episode.

I have heard that it could be a plugin of gnome-do?  How could I figure something like this out?  There must be an easier way than unchecking each of the bazillion boxes one at a time and hoping for the app to run out of control again one day.  Do any of you have similar problems using a particular plugin?

Thank you for your help

---

### Post by kid1000002000 on 2010-07-18
bump

---

### Post by kid1000002000 on 2010-07-21
bump!

---

### Post by stinkeye on 2010-07-22
Quit gnome-do and start it in the terminal with 
```
gnome-do --debug
```
to see if you get any hint from the output.

It runs ok for me (not in dock mode...I use docky for that) 
And the only plugins I use are
Alias
Files and Folders
Gnome Session Management
Shelf

---

### Post by fabounet on 2010-07-23
alternatively you can try **Kupfer**, which is faster than Gnome-Do and  can already do much of the job

---

