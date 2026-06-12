---
title: "Acrobat Reader"
date: 2005-01-17
forum: Desktop Environments
---

### Post by acaus on 2005-01-17
How do I install Adobe reader, whenI clck on the install icon it comes up with licence and acceptance, but it will not install says I don't have permission?

Angus

---

### Post by coolbreeze on 2005-01-17
If I remember correctly the downloaded file comes restricted.  You will have to change the permissions in terminal using su chmod.  Here is what I found on the internet about the chmod command.

[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

---

### Post by acaus on 2005-01-17
I tried the chmod but still no joy, it states that it is unable to write to the folder which I made for it.

---

### Post by coolbreeze on 2005-01-17
Ok you made a folder? That sounds like you didn't install according to the guide.  Check it out.

[http://ubuntuguide.org/#acroread](http://ubuntuguide.org/#acroread)

I don't see anything about a folder.

Let apt install it for you.

sudo apt-get install acroread
sudo apt-get install acroread-plugin

---

### Post by coolbreeze on 2005-01-17
Uh Oh I see acroread package can't be located by apt. Maybe the name is wrong or maybe I need to add a new source to /etc/apt/sources.list.  I'll try and figure it out.

---

### Post by coolbreeze on 2005-01-17
Ok there is something wrong with acrobat reader installation on apt.  The new name of the install is acroread-debian-files (look in Synaptic).  However when i marked it for installation I get an error message that says it depends on acroread but acroread isn't installable.  Maybe some experieenced folks can tell us what's going on and how to fix.

---

### Post by bob k on 2005-01-18
[QUOTE=acaus]How do I install Adobe reader, when clck on the install icon it comes up with licence and acceptance, but it will not install says I don't have permission?

Angus[/QUOTE]

Try xpdf or gpdf. I didn't care much for acroread. I had to accept the user agreement every time I opened a pdf doc, printing didn't work on large documents. Anyway there were more problems than I wanted to solve for a pdf reader.

---

