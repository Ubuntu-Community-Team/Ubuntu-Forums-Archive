---
title: "Create text file with the name as System date"
date: 2010-12-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mahesh123 on 2010-12-20
HI

I want to create a text file with the name as SYSTEM DATE...
for example---28/04/2008:9:11:50.txt
The File name should be allocated on dynamically.....

can u provide the c code for this..

Plese Help me...

---

### Post by iponeverything on 2010-12-20
is this homework?

---

### Post by lykeion on 2010-12-20
@moderator
Shouldn't this be moved to Programming Talk?

First of all forward slashes is for directories. You should replace them with another character like '-', so the filename would be something like *28-04-2008:9:11:50.txt*

In a terminal you can do something like this:
```
touch $(date +"%d-%m-%Y:%T").txt
```

In C you should take a look at the Time.h library and fopen command. Online C reference here: [http://www.acm.uiuc.edu/webmonkeys/book/c_guide/](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/)

---

### Post by mahesh123 on 2010-12-22
Thanku very much for your reply.

I need to append the data from mouse to this text file.So is it possible to send the data from the mouse into the file if opened a file using touch command.Please give me some suggestions regarding this.

---

