---
title: "Apache? Where to post?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by dchurch24 on 2008-02-06
Hi all,

I know this is probably the wrong place to post questions about Apache on Ubuntu, but I can't seem to find a relevent forum.

I have installed 7.10 from scratch as upgrading from 7.04 completely failed.

Anyway, got it all installed and was going through setting up everything from scratch and got to installing Apache with PHP5.  Installed it the same way I always have, but this time, each time I visit a .php file, it tries to download it saying it is: application/x-httpd-php.

I would ideally like it to run the code and display the results of php files in the browser.

What have I done wrong that I normally don't do?

---

### Post by mcduck on 2008-02-06
> **dchurch24 said:**
> Hi all,

I know this is probably the wrong place to post questions about Apache on Ubuntu, but I can't seem to find a relevent forum.

I have installed 7.10 from scratch as upgrading from 7.04 completely failed.

Anyway, got it all installed and was going through setting up everything from scratch and got to installing Apache with PHP5.  Installed it the same way I always have, but this time, each time I visit a .php file, it tries to download it saying it is: application/x-httpd-php.

I would ideally like it to run the code and display the results of php files in the browser.

What have I done wrong that I normally don't do?

Try rebooting the machine if you haven't already done that.. Or perhaps just restarting apache would work as well..

---

### Post by dchurch24 on 2008-02-06
Hi, thanks for the quick response.

I uninstalled again, reinstalled, restarted Apache and hey presto - it works.

Patience was never my strong point ;-)

---

### Post by Aximilli on 2008-02-06
Hey, how does one restart apache anyway?

---

### Post by mcduck on 2008-02-07
```
sudo /etc/init.d/apache2 restart
```
(you can also use "start" and "stop" in the command).

Most of the services can be started, stopped and restarted this way. For example, the graphical desktop can be stopped by running "sudo /etc/init.d/gdm stop"..

---

