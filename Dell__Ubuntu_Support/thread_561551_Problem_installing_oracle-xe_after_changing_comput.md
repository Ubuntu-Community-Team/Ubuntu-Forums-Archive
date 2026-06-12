---
title: "Problem installing oracle-xe after changing computer name"
date: 2007-09-27
forum: Dell  Ubuntu Support
---

### Post by onemojofilter on 2007-09-27
This is a combination oracle/networking question with ubuntu...

I was able to get oracle-xe running perfectly on another old laptop running Feisty Fawn so I'm confused as to why this is such a problem now with a new laptop.

I purchased a Dell Inspiron 1420N with ubuntu 7.04 pre-installed. Everything works great ... except... I had installed Oracle-XE and then decided to change the computer name (because I don't want it known as 'dell').

I changed /etc/hostname and /etc/hosts as well. I tried changing the tnsnames.ora file as well as the listener.ora file under $ORACLE_HOME/network/admin as well... all to no avail.

I re-installed oracle-xe by running 'sudo apt-get remove oracle-xe'  and then removing all extraneous oracle files/directories. 

Re-installed with 'sudo apt-get install oracle-xe'. Still no joy.

Can anyone help?

Thanks!!

---

### Post by lisati on 2007-09-27
I'd be surprised if your woes were directly linked to the name of your computer. As to what to do about it, anyone else?

---

### Post by onemojofilter on 2007-09-28
I resolved this.

Apparently the issue all this time was permissions on a log file that the listener writes to when it tries to come up. Once that was taken care of the database did come up normally.

This after numerous installs/de-installs... Having said that, I must say that on another laptop running ubuntu 7.04 the installation of Oracle-XE was flawless. 

I'm not sure what went wrong but I got the distinct impression after reading several forms on the subject that 90% of the time it's failure of the listener that is to blame.

Oh well (can't find a shrug smiley)...

---

