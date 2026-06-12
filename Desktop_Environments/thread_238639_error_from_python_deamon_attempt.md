---
title: "error from python deamon attempt"
date: 2006-08-18
forum: Desktop Environments
---

### Post by madlan on 2006-08-18
Hi all, 
I am typing the following into the terminal:


python /var/www/SABnzbd/SABnzbd.py -d -f /var/www/SABnzbd/SABnzbd.ini


to try and run the SAB python script as a deamon, but i receive an error message:

Error:
I Refuse to fork without a log directory!


Do you have any idea what the problem is?

Regards,
Alan.

---

### Post by FerGeCo on 2006-10-06
Sounds like SABnzbd can't find it's log directory ..

Did you specify it in the config file ?
and did you create the directory? (SABnzbd doesn't create it for you)

---

