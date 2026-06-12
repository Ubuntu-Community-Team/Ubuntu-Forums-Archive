---
title: "Root can't write to MySQL database"
date: 2011-10-19
forum: Desktop Environments
---

### Post by facelikebambi on 2011-10-19
Hi

I run local installs of PHP applications (mostly Drupal) for web development.

I just installed Ubuntu 11.10, set up apache and imported some databases into MySQL (using phpMyAdmin). 

My local web applications connect to the databases as root and can access tables no problem... until I edit or change anything that writes back to the database. Then it just doesn't happen.

If I manually edit a field in phpMyAdmin (logged in as root), it works fine. So I think there's a permissions issue somewhere?

Here's a listing of the database files in var/lib/mysql:

[IMG]http://www.permissiontoquit.com/mysql.png[/IMG]

I'm a total newb with linux file permissions and ownership - does this look correct?

Thanks!

---

### Post by facelikebambi on 2011-10-19
hmm as a test, I created a new database in phpMyAdmin and my PHP scripts could write to it (I was able to install Drupal). 

But within 2 minutes, the problem came back and Drupal could only 'read' the data. This is seriously weird!

---

