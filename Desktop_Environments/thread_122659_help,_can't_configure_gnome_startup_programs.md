---
title: "help, can't configure gnome startup programs"
date: 2006-01-28
forum: Desktop Environments
---

### Post by austin on 2006-01-28
I go to "Sessions" -> "Startup Programs" -> "Add" and (for a simple test) enter /usr/bin/goobox. When I close the Sessions-Window and open it again, the entry (goobox) is gone.

What's that?

---

### Post by austin on 2006-01-30
oh, maybe it's because I turned off my sudo priviliges. But I'm not at the box right now ... I'll try later ...

... NO, doesn't work with sudo-rights either

---

### Post by netguard on 2006-05-25
Hi, I am new to Linux.

I am experiencing the same problem. I have checked the issue on the root account and it's ok so I guess this problem has something to do with my profile only.
Maybe some permissions of a file to which gnome-session-properties is writing were changed somehow. I can't seem to track this down.
     
Would appreciate some incites...](*,)

---

### Post by netguard on 2006-05-25
OK

I think I got this figured out. as I said, I am new to linux so I am not sure thi sis the best approch but it did the work.
I found the the file ~/gnome2/sessions hold a list of directives about startup programs that pretty much matched the list in gnome-sessions-properties.

Since root user had no problem configuring this I thought this could be permissions related after manually toying with this file's contents and getting the results I wanted. 
Moreover,  I only recently installed Ubuntu I figure the only major changes I have made where during updates of the system and such so I figured one of the updates has changed this file's permissions.

I changed the file's from 644 to 664, deleted the manuall changes I have made for my tests and configured as usuall with gnome-sessions-properties. changes are now saved.

I hope this helps.

---

### Post by netguard on 2006-05-25
sorry for the typo...

that's ~/.gnome2/session

---

