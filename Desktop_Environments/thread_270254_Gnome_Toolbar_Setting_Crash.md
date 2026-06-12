---
title: "Gnome Toolbar Setting Crash"
date: 2006-10-02
forum: Desktop Environments
---

### Post by aldegaz on 2006-10-02
Hi,

Im using the Edgy Beta release of Ubuntu, but, I guess I can get an answer here for this problem.

I was fooling around with the Toolbar settings and when changing the pixels on the top toolbar Gnome crashed to the Log-on screen.

I cant log as anything but the terminal, I have tried to log on as safe gnome but with no luck.

I have searched for a terminal code to get to restore gnome to its defaults but with no luck.

Could you guys help me get Gnome to its default settings? Or at least get the toolbar pixels down (wich was I think the reason of the permanent crash)?

thanks and sorry for posting about edgy here, I didnt know what else to do.

---

### Post by black hole sun on 2006-10-02
Post the error message it gives you, also this should be in this forum [http://ubuntuforums.org/forumdisplay.php?f=144](http://ubuntuforums.org/forumdisplay.php?f=144)

---

### Post by aldegaz on 2006-10-03
> **black hole sun said:**
> Post the error message it gives you, also this should be in this forum [http://ubuntuforums.org/forumdisplay.php?f=144](http://ubuntuforums.org/forumdisplay.php?f=144)

I have just posted in the edgy forusm with the link you gave me. This could be usefull with Dapper too, so I would still be a good Idea to leave this thread open.

I will post my solutcion when I get one.

---

### Post by aldegaz on 2006-10-03
OK, I managed to RESTORE completely GNOME with the following:

sudo apt-get remove ubuntu-desktop

Wich didnt take much but seconds, and then

sudo apt-get install ubuntu-desktop

I hope this thread gets some help out there

---

