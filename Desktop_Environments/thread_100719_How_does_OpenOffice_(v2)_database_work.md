---
title: "How does OpenOffice (v2) database work?"
date: 2005-12-08
forum: Desktop Environments
---

### Post by joepotter on 2005-12-08
Has anyone been able to get the new database portion of OpenOffice working? I do not seem to be able to get it to do anything.

Thanks.

---

### Post by GrumpyBob on 2005-12-08
My suggestion would be to ask your question over at the OOo forums at [www.openoffice.org](www.openoffice.org).  In my experience, you can be assured of a rapid and detailed response.

There is a Base forum.  Have a look at [http://www.oooforum.org/forum/viewtopic.phtml?t=25060](http://www.oooforum.org/forum/viewtopic.phtml?t=25060) 
for example.

Robert

---

### Post by joepotter on 2005-12-08
[QUOTE=GrumpyBob]My suggestion would be to ask your question over at the OOo forums at [www.openoffice.org](www.openoffice.org).  In my experience, you can be assured of a rapid and detailed response.

There is a Base forum.  Have a look at [http://www.oooforum.org/forum/viewtopic.phtml?t=25060](http://www.oooforum.org/forum/viewtopic.phtml?t=25060) 
for example.

Robert[/QUOTE]



I posted here because I can not get the program to even open. I would like to just see the program open one time.

Perhaps the Debian user list would be of more help, but I think we might have a Ubuntu packaging problem. (perhaps not)

Thanks.


EDIT: I forgot to say that OpenOffice is looking for "libsqldb2" and can not find it, and that stops one from doing anything with the program as far as I can see.

---

### Post by GrumpyBob on 2005-12-08
Oh, I apologise!
I'll give it a whirl and try it myself!

Robert

Edit: seems to work for me.  A little slow, though.

---

### Post by matthew on 2005-12-08
[quote=joepotter]EDIT: I forgot to say that OpenOffice is looking for "libsqldb2" and can not find it, and that stops one from doing anything with the program as far as I can see.[/quote]You could try to install libsqldb2 using synaptic or "sudo apt-get install libsqldb2" and see if that take care of the problem.

I'm using the version of OpenOffice from the Breezy repos with no problems.

---

### Post by joepotter on 2005-12-09
[QUOTE=matthew]You could try to install libsqldb2 using synaptic or "sudo apt-get install libsqldb2" and see if that take care of the problem.

I'm using the version of OpenOffice from the Breezy repos with no problems.[/QUOTE]



I found the trouble --- turns out the configuration files got corrupted somehow and it would not work like it is supposed to do. I did a "rm -rf .open*" and all started working as billed in various tutorials.

Odd how that could happen on one computer, but not several others.

---

### Post by matthew on 2005-12-09
[quote=joepotter]I found the trouble --- turns out the configuration files got corrupted somehow and it would not work like it is supposed to do. I did a "rm -rf .open*" and all started working as billed in various tutorials.

Odd how that could happen on one computer, but not several others.[/quote]Cool. Glad you figured it out!

---

