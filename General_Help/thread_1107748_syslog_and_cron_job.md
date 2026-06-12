---
title: "syslog and cron job"
date: 2009-03-27
forum: General Help
---

### Post by abasel on 2009-03-27
I am seeing heaps of the following lines in /var/log/syslog

Mar 27 06:50:01 moodle /USR/SBIN/CRON[12000]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)

But I know longer have the /var/www/moodle/eportfolio directory.

Where do I find who is call the following cron and how do I remove it?

Mar 27 06:50:01 moodle /USR/SBIN/CRON[12000]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:51:01 moodle /USR/SBIN/CRON[12004]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:52:02 moodle /USR/SBIN/CRON[12008]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:53:01 moodle /USR/SBIN/CRON[12012]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:54:01 moodle /USR/SBIN/CRON[12016]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:55:01 moodle /USR/SBIN/CRON[12020]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:56:01 moodle /USR/SBIN/CRON[12024]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)
Mar 27 06:57:01 moodle /USR/SBIN/CRON[12028]: (www-data) CMD (php /var/www/moodle/eportfolio/lib/cron.php)

---

