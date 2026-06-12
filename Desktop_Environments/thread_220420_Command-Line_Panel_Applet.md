---
title: "Command-Line Panel Applet?"
date: 2006-07-21
forum: Desktop Environments
---

### Post by MindSpore on 2006-07-21
After upgrading to dapper, I discovered that the command-line applet which docks to the panel is no longer (at least obviously) included in Ubuntu.  YES I know about alt+f2, however i want my handy docked command-line back.  I loved being able to just click up on the panel and do a quick "killall esd" or whatever.

Anyone know where this disappeared to?

---

### Post by bDerrly on 2006-07-21
Right click on the panel and click "Add to panel", then search through the applets for the command line one. It may be called something else but it is there because I've got it at home.

---

### Post by MindSpore on 2006-07-24
If you could tell me the name of the application i would really appreciate it.  FYI, I am **not** talking about the "run application" applet.  I am talking about an actual command line that is docked on the panel.

---

### Post by tturrisi on 2006-07-24
Applications > Accessories > Terminal > rt click & select "Add this launcher to panel".

---

### Post by pracslipkerm on 2006-08-02
> **MindSpore said:**
> If you could tell me the name of the application i would really appreciate it.  FYI, I am **not** talking about the "run application" applet.  I am talking about an actual command line that is docked on the panel.

I agree with MindSpore. I too REALLY miss this applet! It was great being able to put code into a box and execute. 
This is not just a link to a terminal window but a textbox on the panel that executes 1 line of commands as if from the terminal. Please someone show us where it went!!!
Cheers
  Steve :-)
PS. Check out this thread 
[http://ubuntuforums.org/showthread.php?t=150848&highlight=Applet+Command+line](http://ubuntuforums.org/showthread.php?t=150848&highlight=Applet+Command+line)
- apparently it got upgraded and renamed - but you need to install it. I did ```
sudo aptitude install deskbar-applet
```
, tried it out and it works!

---

### Post by Steven_B on 2006-08-02
I think the "mini-commander" has been replaced with "deskbar".  It's called "deskbar-applet" in the repositories.  By default, it also has options to search Google, Amazon, etc, for the keywords, but this can be changed to be only a command line.

---

