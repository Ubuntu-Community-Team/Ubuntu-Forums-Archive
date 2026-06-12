---
title: "Disable logging in Apache 2 Ubuntu 9.04"
date: 2009-09-04
forum: Desktop Environments
---

### Post by headlice on 2009-09-04
Hi,

How do i go about disabling logging in Apache2?

I edited /etc/apache2/apache2.conf and commented out all lines of logging, yet apache2 wont start.

It says this:

Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/error_log.

How is it looking for an error log when I commented out the logging?

Thanks!

---

### Post by bear24rw on 2009-09-04
try removing these lines:
```

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

```

from

/etc/apache2/site-enabled/000-default

no idea if that will work but worth a shot

---

### Post by headlice on 2009-09-04
Did it.  Didnt work.  Same error message......

---

### Post by bear24rw on 2009-09-04
did you add the stuff back into the config when you first got the error message?

---

### Post by headlice on 2009-09-04
> **bear24rw said:**
> did you add the stuff back into the config when you first got the error message?

All I did was comment it out, so it is there but just commented.

The reason why I dont want logging is because it is on a solid state disk and  have my /var/log directory mounted on tmpfs.

Hmmmm, would I be able to point the logs to tmpfs?

---

### Post by bear24rw on 2009-09-04
> **headlice said:**
> 
The reason why I dont want logging is because it is on a solid state disk and  have my /var/log directory mounted on tmpfs.


wait, if your alreading running them on a tmpfs whats the problem, they are writing to ram not your ssd..

---

### Post by headlice on 2009-09-04
> **bear24rw said:**
> wait, if your alreading running them on a tmpfs whats the problem, they are writing to ram not your ssd..

so wait, I dont have to manually point logs to tmpfs?  Everything that is pointing at /var/log will find it in tmpfs?

---

### Post by bear24rw on 2009-09-04
Yeah it should if your mounted /var/log to a ram disk..

---

### Post by headlice on 2009-09-04
> **bear24rw said:**
> Yeah it should if your mounted /var/log to a ram disk..

I do have it mounted there, but it may not be working because if it ever gets shut down, /var/logs/[whatever is after this] gets erased.

.....

I think I know what to do!

Ill specify /var/log/apache2 to mount to tmpfs in /etc/fstab

---

### Post by bear24rw on 2009-09-04
it supossed to get erased.. its in ram..

---

### Post by headlice on 2009-09-04
> **bear24rw said:**
> it supossed to get erased.. its in ram..

right, but all I have specified to mount in tmpfs is /var/log

apache is looking for /var/log/apache2 to put the logs in.  If I install apache, it runs just fine because it creates /var/log/apache2

but when I reboot, /var/log/apache2 is gone and throws the error.

To remedy this, Ill specify /var/log/apache2

---

