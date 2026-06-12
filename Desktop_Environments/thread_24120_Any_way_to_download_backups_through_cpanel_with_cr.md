---
title: "Any way to download backups through cpanel with cron?"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Trickyphillips on 2005-04-05
This may be a strange question, but I'm looking for a way to download a database backup through cpanel every 12 hours with cron. The database backup is at "http://www.mysite.com:2082/getsqlbackup/vbulletin.gz", and is password protected with an htaccess file. If possible, I'd like the database to go into a folder named something like '[date], [time]'.

Thanks! :smile:

---

### Post by Jad on 2005-04-05
I think it wont work, as this url /getsqlbackup/file.gz the file.gz generated on-the-fly 
what I suggest to run a cronjob to backup yoursql, and set it inside public_html, and then you will have to setup a cron on your local machine to wget it.

---

### Post by Trickyphillips on 2005-04-05
Hmm. Thanks. I don't have full access to the server (My host doesn't even have a telnet server up. :(), but I'll talk to them about it.

Thanks again. :)

---

### Post by Jad on 2005-04-06
If you search  hotscripts.com for some backup tools you will find some php based tools that you can run to backup your db, so what you need is only to have access to cron-job which you have it in cpanel control panel to  run the php backup script.

---

