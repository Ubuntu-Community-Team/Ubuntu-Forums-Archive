---
title: "Where is the &quot;File Types and Programs&quot; preference tool?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by taj on 2005-10-31
[In this (err Warty...) thread]("http://ubuntuforums.org/showthread.php?t=9895") :oops:  I yesterday brought up the following problem:
I installed Openoffice 2.0 according to [this thread]("http://ubuntuforums.org/showthread.php?t=80392"), and removed Ooo1.9 (shown as Openoffice2 to make our life easier, I guess). Now every time I double click e.g. a Word document in Nautilus it wants to open with Openoffice2 (Ooo1.9), unless I rightclick the document and choose Openoffice2.0 (the real 2.0).
Ubuntu Help states that I need to solve the problem: Gnome's System -> Preferences -> File Types and Programs, but it's not there. I assume it's part of the standard Gnome system.
So, how can I install the "File Types and Programs" preference tool that I need, or where can I find its function, or how can I get around this problem with command line? I strongly suggest to include it into the next release.

---

### Post by paddyg on 2005-10-31
have you tried

rightclick properties-->open with-->add   ?

---

### Post by taj on 2005-10-31
Yep, I tried that.
Right-clicking gives the following list:

Open with "OpenOffice.org2 writer"
---separator---
Open with "OpenOffice.org2.0 writer"
Open with Other Application
(etc.)

NB "OpenOffice.org**2** writer" = OOo1.9; "OpenOffice.org**2.0** writer" = OOo2.0

Since I have removed OOo1.9, "Open with Other Application" only gives OpenOffice.org2.0 writer as an option. I cannot set it as default. For that, according to Help I'll need  "File Types and Programs", which lacks in ubuntu, at least since Warty. I have tried all menu options in Nautilus, but nothing works****

---

### Post by poptones on 2005-10-31
Right click on the file and select "properties"
Click the "open with" tab
Find (or add) "Open Office 2.0"
Click the radiobutton to make it default

Now when you right click the other options will be below OO2, and OO2 will be the "default" means of opening the file.

---

### Post by taj on 2005-11-02
Thanks. That solved the problem.

I did all you said long before, but I never saw that in fact the radiobutton was unselected.

---

