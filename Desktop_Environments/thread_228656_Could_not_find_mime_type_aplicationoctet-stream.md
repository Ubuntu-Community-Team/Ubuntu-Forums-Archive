---
title: "Could not find mime type aplication/octet-stream"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Tosa on 2006-08-03
I'm not sure, but I think the message ***Could not find mime type aplication/octet-stream*** started a couple of days ago when Gwenview was updated. It's really very anoying. It shows when I turn my Pc on, and then every time I start Gwenview. It also shows when Konqueror starts and when I move the mouse pointer over files. Instead of a thumbnail of a file content I get that @#$% message. When I click on a bitmap in Konqueror, Gwenview opens it, but not before I get the message.
What's Going on ?:confused:

---

### Post by the-linux-guy on 2006-08-03
Fire up KControl, go to KDE components, go to file associations, select application and manually add a "new type" named octet-stream, leave all other fields blank as they are... click save and logout/login again...
Problem solved. Have had this annoyance a few times allready and not just in Ubuntu (Fedora Core and Mandrake seem to have this same bug)...

With kind regards,

Eddy

---

### Post by Tosa on 2006-08-03
Thanks a million Eddy!

It works!! :D

---

### Post by rejser on 2006-09-05
Got the same problem, solved it, tnx alot!

---

### Post by praddie on 2006-09-17
Thanks Eddy, it worked for me too.....

---

### Post by beerorkid on 2006-10-03
ok I am getting this but in gnome.  cant figure out where to change this.  any ideas?

EDIT: Start the Control Center With sudo kcontrol in terminal and open KDE Components/File Associations,
Expand "application", you will probably see that there's no entry for "octet-stream".
Click on "Add...", for "Group" select "application" and for "Type Name" fill in "octet-stream". This should fix it.
Regards
Sharke

---

