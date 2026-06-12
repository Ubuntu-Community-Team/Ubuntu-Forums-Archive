---
title: "What are the standard user and group names for?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Jenske on 2006-06-09
Hi,

I wonder what the different group names and user names that come with Ubuntu Dapper Drake stand for? Does a list exist, mentioning all these things and telling me what the different groups/users are for?

(It took me ages to find out that in order to give scanner access to another user on my computer, I had to add him to the "lp"-group. I can see some logic in a group name like "scanner", but "lp"???????)

Jens (Belgium)

---

### Post by hw-tph on 2006-06-09
[Here](http://www.togaware.com/linux/survivor/Standard_Groups.html) is a list of the groups with brief descriptions what good they do.

As for your scanner access problem - is your scanner one that connects to the parallell port? lp is short for "line printer" and printers are traditionally connected using the parallell port (aka "printer port"). In order to use anything connected to the parallell port you must be part of the lp group since the parallell port device (/dev/parport0) should be owned by root:lp. "root:lp" means root is the owner and lp is the group the file belongs to. You will come across this kind of terminology when using the chown command and similar ones.


Håkan

---

### Post by Jenske on 2006-06-11
[QUOTE=hw-tph] (...)
As for your scanner access problem - is your scanner one that connects to the parallell port? lp is short for "line printer" and printers are traditionally connected using the parallell port (aka "printer port"). In order to use anything connected to the parallell port you must be part of the lp group since the parallell port device (/dev/parport0) should be owned by root:lp. "root:lp" means root is the owner and lp is the group the file belongs to. You will come across this kind of terminology when using the chown command and similar ones.
Håkan[/QUOTE]

=> Correct! I've added all users on my computer to the "lp" group and now anybody (belonging to this group) can access the scanner.
And also correct: I have a flatbed scanner (Lifetec (=Medion)) connected to parallel port. In turn the printer (HP Deskject 840C) is connected to the scanner.

This combination now works perfectly.

---

