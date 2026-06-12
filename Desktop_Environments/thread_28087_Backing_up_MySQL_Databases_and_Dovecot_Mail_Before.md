---
title: "Backing up MySQL Databases and Dovecot Mail Before Upgrading to Hoary"
date: 2005-04-18
forum: Desktop Environments
---

### Post by Levander on 2005-04-18
Have some decently valuable data on my Ubuntu box and wanting to back it up before I upgrade to hoary, two things I don't really know how to back up well, mysql databases and my mail.

With the mysql databases, if I just back-up /var/lib/mysql, will everything restore okay to Hoary after I get it installed if something goes wrong in the interim?

With my mail, I'm running dovecot so I can check my mail via IMAP and am using Thunderbird as a client to check it under XP and Ubuntu.  I see all my mailbox folders in ~/mail, except for the Inbox.  Where's the Inbox?  For the rest of the stuff, can I just backup ~/mail and be fine after the upgrade? Even if something goes wrong and I have trouble installing it?

---

### Post by speedman on 2005-04-18
I'm not familiar with dovecot, but you can backup and restore your mysql dbs as such:

To dump a db:

mysqldump -u root -pXXX db_name > backup.sql

To restore a db from a sql file:

mysqladmin -u root -pXXX create db_name

mysql -u root -pXXX db_name < backup.sql

Replace XXX with your password and db_name with the name of your database.

HTH


Regards,

SM

---

### Post by Levander on 2005-04-19
Okay, thanks speedman.  That's how I'll backup the databases.

Also, I found the dovecot Inboxes for dovecot users.  They're in /var/mail.  Only thing that's kind of strange is that even after I delete a message from my Inbox using the IMAP client, the messages are still in that Inbox file in /var/mail for awhile at least.  And, I see nothing in that file that indicates that that message has been moved to another folder.  Another folder, in the case of deletion would be Trash.  It's like there must be another dovecot file indicating which messages have been moved out of Inbox.

Still trying to figure out how to backup dovecot.

---

