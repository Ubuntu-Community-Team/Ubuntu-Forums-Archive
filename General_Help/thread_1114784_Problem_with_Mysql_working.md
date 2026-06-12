---
title: "Problem with Mysql working"
date: 2009-04-03
forum: General Help
---

### Post by chetan.sharma on 2009-04-03
Hey people i am getting problem with my apache server..
I installed all the packages off mysql,php and apache required in ubuntu 
but when i am running the localhost and trying to open a file it automatically starts  to save the file...!!
If any body got an answer plz help me out....!!! :?

---

### Post by ahop on 2009-04-03
It sounds to me like your browser thinks you are downloading a document.  Which means that it is not a problem with MySQL, but rather a problem with your Apache/PHP setup.  PHP is not being executed.

What steps did you take?  Did you install all the components separately, or did you use a LAMP package?

---

### Post by hikaricore on 2009-04-03
Why exactly is this in the WINE forum?  Thread moved...

---

### Post by hyper_ch on 2009-04-03
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

