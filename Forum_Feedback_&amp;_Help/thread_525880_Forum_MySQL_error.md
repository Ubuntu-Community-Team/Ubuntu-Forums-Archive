---
title: "Forum MySQL error"
date: 2007-08-14
forum: Forum Feedback &amp; Help
---

### Post by mssever on 2007-08-14
Just now as I was preparing to post a new thread, I saw the following error message (after I tabbed out of the title box):
```
<!-- Database error in vBulletin 3.6.8: Invalid SQL: SELECT * FROM ruleshack WHERE (fileurl LIKE 'http://ubuntuforums.org/ajax.php?do=getsimilarthreads&title=BadgeEntry:%20New%20children's%20ministry%20resource%20--%20beta%20testers%20wanted' AND exactmatch = 1 ) OR (fileurl LIKE 'http://ubuntuforums.org/ajax.php%' AND exactmatch = 0 ) AND active = 1 ORDER BY ruleid; MySQL Error : You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 's%20ministry%20resource%20--%20beta%20testers%20wanted' AND exactmatch = 1 ) ' at line 2 Error Number : 1064 Date : Wednesday, August 15th 2007 @ 01:51:59 AM Script : http://ubuntuforums.org/ajax.php?do=getsimilarthreads&title=BadgeEntry:%20New%20children's%20ministry%20resource%20--%20beta%20testers%20wanted Referrer : http://ubuntuforums.org/newthread.php?do=newthread&f=168 IP Address : 75.106.9.198 Username : mssever Classname : vB_Database_Slave_MySQLi -->
```It appears to me that the apostrophe (single quote) in my title wasn't escaped properly. I'm attaching a screenshot of the complete effect. Note how the error messed up the screen.

By the way, in case it's relevant, I'm using the Epiphany browser.

---

### Post by angryfirelord on 2007-08-18
Does the error come up anymore? I haven't seen it yet.

---

### Post by mssever on 2007-08-19
I haven't seen it again. But then I haven't tried to reproduce it, either.

---

