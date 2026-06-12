---
title: "foloowing a howto to enable mod-python in apache2"
date: 2020-06-08
forum: Debian
---

### Post by Hotchilli on 2020-06-08
Here is the url.

[https://www.cyberciti.biz/faq/ubuntu-mod_python-apache-tutorial/](https://www.cyberciti.biz/faq/ubuntu-mod_python-apache-tutorial/)

   

Give your account permission to access the scripts:

$ sudo chown yourname:www-data /var/www/py

what does the above  line mean i thought it should read
root:root 4096 py  in /var/www

---

### Post by CelticWarrior on 2020-06-08
> Give your account permission means your account, not root.

---

### Post by SeijiSensei on 2020-06-08
> **Hotchilli said:**
> 
$ sudo chown yourname:www-data /var/www/py

what does the above  line mean i thought it should read
root:root 4096 py  in /var/www

These steps create a directory to house the Python scripts that you can write into. That's why its owned by "yourname."  The later steps tell Apache to use mod-python to handle files that end in .py

---

### Post by Hotchilli on 2020-06-08
ok  followd the howto and did as suggested but no hello world 
apache err log

[Mon Jun 08 20:08:54.058339 2020] [:error] [pid 8640:tid 140256318812224] python_init: Python version mismatch, expected '2.7.5+', found '2.7.13'.
[Mon Jun 08 20:08:54.058438 2020] [:error] [pid 8640:tid 140256318812224] python_init: Python executable found '/usr/bin/python'.
[Mon Jun 08 20:08:54.058442 2020] [:error] [pid 8640:tid 140256318812224] python_init: Python path being used '/usr/lib/python2.7:/usr/lib/python2.7/plat-x86_64-linux-gnu:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Mon Jun 08 20:08:54.058450 2020] [:notice] [pid 8640:tid 140256318812224] mod_python: Creating 8 session mutexes based on 6 max processes and 25 max threads.
[Mon Jun 08 20:08:54.058452 2020] [:notice] [pid 8640:tid 140256318812224] mod_python: using mutex_directory /tmp 
[Mon Jun 08 20:08:55.004433 2020] [mpm_event:notice] [pid 8640:tid 140256318812224] AH00489: Apache/2.4.25 (Debian) mod_python/3.3.1 Python/2.7.13 configured -- resuming normal operations
[Mon Jun 08 20:08:55.004567 2020] [core:notice] [pid 8640:tid 140256318812224] AH00094: Command line: '/usr/sbin/apache2'

---

### Post by Hotchilli on 2020-06-09
ok i can answer my own question to a point 

the debian apache version I amusing requires 2.7.5 and I have 2.7.13, so one might assume that it is very specific about the version it needs or that the apache implementation is incorrect in being so specific, second part would be why it needs to use what in effect is a out of support version now,?

How to proceed installing mod-python?

---

### Post by SeijiSensei on 2020-06-09
Are you running Ubuntu or Debian?

If you're running Ubuntu, you should install everything from the Ubuntu repositories.  Mixing-and-matching across distributions will only lead to problems.  Same holds true if you're running Debian, in which case your question would be better posted here: [https://ubuntuforums.org/forumdisplay.php?f=161](https://ubuntuforums.org/forumdisplay.php?f=161). Report your post and ask a moderator to move it.

---

### Post by howefield on 2020-06-09
Thread moved to the "*Debian*" forum.

OP is using Debian 9 on a remote vps.

---

