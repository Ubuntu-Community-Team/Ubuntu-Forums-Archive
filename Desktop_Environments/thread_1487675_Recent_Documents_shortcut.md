---
title: "Recent Documents shortcut"
date: 2010-05-19
forum: Desktop Environments
---

### Post by StolenPie on 2010-05-19
I would like to put a recent documents shortcut somewhere on my Gnome Panel, like as an applet or something like that. 

Is there a way of doing this?

---

### Post by vangelas on 2010-11-06
Better late than ever I guess.
You can install desklets from the repository and then put a shortcut on your desktop. Also in your home folder you have a file called .recently-used.xbel. 
I find neither of these very useful though :smile:

---

### Post by Enigmapond on 2010-11-06
You could always install Gnome Activity Journal and then just put that on the panel or desktop..
[http://www.webupd8.org/2010/01/install-gnome-activity-journal-and.html](http://www.webupd8.org/2010/01/install-gnome-activity-journal-and.html)

EDIT: Didn't realize this thread was from May....LOL

---

### Post by holiday on 2010-11-06
You could look into find.

Google on "man find".

In the console, using find, you can list files by exactly how recently.

find . -ctime 1 -name *.txt

will list every .txt file that's been changed in the last 24 hours. 

Change the 1 to .1 and the list will show only those files changed in the last 2.4 hours. There are many switches. 

You can change the -name argument to anything or you can run without it.

find is one of the most useful Unix utilities and you will do well to discover its power.

---

