---
title: "how do you install themes in Ubuntu 11.10?"
date: 2011-10-20
forum: Desktop Environments
---

### Post by cortman on 2011-10-20
How do you install themes in Ubuntu 11.10?
I guess a better question would be how to do so in Gnome 3.2 Classic.
Before I could just drag-drop tar.gz files into the theme tab, but there is no theme tab anymore.
???

---

### Post by Frogs Hair on 2011-10-20
I use the manual method with Unity 11.10 . I download , extract the package , and check all folders to make sure everything is extracted . 

I drag the folders I want to use to the desktop and use the following .```
gksu nautilus
```

I migrate to file system / usr / share / themes and drag the folders from the desktop to the themes folder .

Open Gnome Tweak tool / Advanced Settings installed from the software center and select theme .

I have tried creating a .themes folder in home / hidden folder without success . I use gksu nautilus to have permission to move the folders into the file system . If there is a way to drag and drop I have not found it yet .

---

### Post by randywilharm on 2011-10-20
Try:

gksudo nautilus


It's safer with graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Frogs Hair on 2011-10-21
Update ! If you are a single user creating a .themes or .icons folder in home hidden folders and placing the themes / icons there should also work . The theme I originally  attempted this with was out of date .

I tried again with a recently updated theme and it worked fine . If you want to share with all users continue to use usr / share / themes  or icons in the file system

---

