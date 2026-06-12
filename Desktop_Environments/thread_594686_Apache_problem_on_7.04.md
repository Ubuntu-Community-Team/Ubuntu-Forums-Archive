---
title: "Apache problem on 7.04"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Miroslav Dostanic on 2007-10-28
I installed apache2 with **sudo apt-get install apache2**, but it doesn't working. When i type [http://localhost/](http://localhost/) in firefox, it returns

**[SIZE="3"]Unable to connect[/SIZE]**

Firefox can't establish a connection to the server at localhost.

---

### Post by Pro4Life on 2007-11-15
I have the exact same problem on my Ubuntu.

---

### Post by D-EJ915 on 2007-11-16
is apache running?

sudo /etc/init.d/apache2 start

also make sure in /etc/hosts that 127.0.0.1 is localhost

---

### Post by lightstream on 2007-11-17
another thing to check out is the apache error log at /var/log/apache2

it should list any errors encountered at start up

---

### Post by pneaveill on 2007-12-16
> **D-EJ915 said:**
> is apache running?

sudo /etc/init.d/apache2 start

also make sure in /etc/hosts that 127.0.0.1 is localhost

I am having the same issue as here in this thread and hoping it is still active and not archived already.

```

127.0.0.1    localhost
127.0.0.1    dualboot1
```

```
sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                              (98)Address already in use: make_sock: could not bind to address 0.0.0.0:8070
no listening sockets available, shutting down
```

Thanks in advance

---

### Post by D-EJ915 on 2007-12-18
You need to go to /etc/apache2/ports.conf and add "Listen **" where ** is the port number, it should have 80 there as default so that is odd that it gave you that message.

---

### Post by Dixon Bainbridge on 2007-12-18
Or install Xampp. I find it easier.

---

### Post by pneaveill on 2007-12-29
> **Dixon Bainbridge said:**
> Or install Xampp. I find it easier.

Do you have ideas on how to remove the old hangovers and leftovers from the original apache install? I tried doing the apt-get remove --purge apache and all that in another part of the forum here and still get this:

>  /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.5a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Your /etc/hosts is not okay. I will fix it.
XAMPP: See also [http://www.apachefriends.org/faq-lampp-en.html#failed](http://www.apachefriends.org/faq-lampp-en.html#failed)
XAMPP: Next try...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of '192.168.1.25_8070_dualboot1'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'

192.168.1.25 is the local IP address of this computer and the name of it is dualboot1. My reason for doing the *:8070 was because I have DSL and the ISP often does not allow inward access lower than 1000. It was suggested to me in another forum to use *:8070 instead of the *:80. If there is a better option, I would love to hear about it.

---

### Post by slowcoach on 2007-12-29
> **pneaveill said:**
> Do you have ideas on how to remove the old hangovers and leftovers from the original apache install? I tried doing the apt-get remove --purge apache and all that in another part of the forum here and still get this:
192.168.1.25 is the local IP address of this computer and the name of it is dualboot1. My reason for doing the *:8070 was because I have DSL and the ISP often does not allow inward access lower than 1000. It was suggested to me in another forum to use *:8070 instead of the *:80. If there is a better option, I would love to hear about it.
To remove Xampp just go to the /opt directory and delete the lampp directory, that's it, all gone.

To install Lampp in Gutsy, open Synaptic Package Manager, select Edit at the top menu, select Mark Packages by Task...  select Lampp from the list then proceed with synaptic as if you are installing any usual package.

---

### Post by pneaveill on 2008-01-08
Thanks for the input so far. 

Sorry for the delay, been really sick for a while.

Seems like everything loaded so far, just wondering what I need to do now.

---

