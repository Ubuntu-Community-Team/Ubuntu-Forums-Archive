---
title: "Trying to install"
date: 2009-04-01
forum: General Help
---

### Post by happyhacker on 2009-04-01
Can anyone help with the failure of this install via webmin? Failure at bottom of output.

Downloading [http://www.webmin.com/download/modules/shellinabox.wbm.gz](http://www.webmin.com/download/modules/shellinabox.wbm.gz) (325 bytes) ..
Downloading [http://download.webmin.com/download/modules/shellinabox.wbm.gz](http://download.webmin.com/download/modules/shellinabox.wbm.gz) (159522 bytes) ..
     Received 1024 bytes (0 %)
     Received 16384 bytes (10 %)
     Received 32768 bytes (20 %)
     Received 48128 bytes (30 %)
     Received 64512 bytes (40 %)
     Received 79872 bytes (50 %)
     Received 96256 bytes (60 %)
     Received 112640 bytes (70 %)
     Received 128000 bytes (80 %)
     Received 144384 bytes (90 %)
     Received 159522 bytes (100 %)
.. download complete.

Failed to install package : Not a valid compressed or gzipped Debian DPKG file

---

### Post by Sam Lars on 2009-04-03
That's odd... it looks like you're running the update through Webmin?  What version are you at?

---

### Post by happyhacker on 2009-04-06
I installed webmin around Jan this year. Sorry but I am not in office untill wed. 8th.

Did you want the webmin version?
Are you implying I should not be able to do this?

I am trying to install PHPMyAdmin to control my Mysql DB.

---

### Post by Sam Lars on 2009-04-06
Ubuntu has PHPMyAdmin in the repos, you should be able to install it through at least the command line in Webmin.  You could also use the Software Packages tool under System.

---

### Post by happyhacker on 2009-04-06
The command line in Webmin will not accept actions which require replies (like: do you accept the extra space required?) or if I request phpmyadmin in the package section it does not find it!

Any other suggestions welcome (will I really have to connect a display and keyboard to my system?). Perhaps Webmin is not up tom it!

---

### Post by Sam Lars on 2009-04-06
You should be able to do an apt-get -y or --force-yes to get rid of the prompts.
If you can ssh into the system, that would be better.

---

### Post by happyhacker on 2009-04-08
Thanks for all the help. I managed to get Webmin to install via the packages (this time it found phpmyadmin). It used force in the command line automatically. Now all I have to do is work out how to access it. Thanks.

---

