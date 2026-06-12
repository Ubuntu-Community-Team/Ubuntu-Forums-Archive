---
title: "no moodle: internal server error - php?"
date: 2007-01-01
forum: Education &amp; Science
---

### Post by which_dan on 2007-01-01
Hi all, I have just upgraded my moodle in upgrading my ubuntu install from breezy badger to dapper drake (this brings moodle to 1.5.3 - I don't know what breezy's moodle version was).
After the install, I find an attempt to get into my local moodle gives me a 500 Internal Server error:


Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.


Apache/2.0.55 (Ubuntu) Server at localhost Port 80


which is reported in the apache error log as:

[Sun Dec 31 10:34:33 2006] [alert] [client 127.0.0.1] /usr/share/moodle/.htaccess: Invalid command 'php_flag', perhaps mis-spelled or defined by a module not included in the server configuration

/usr/share/moodle/.htaccess looks fine (the line responsible is probably the following; there are a few flags set but all look pretty similar):

php_flag magic_quotes_gpc 1

Can anyone help me out with this?

I'm using:
moodle 1.5.3
php5 5.0.5 (including php5-cgi, php5-mysql php5-gd at the same version)
apache2 2.0.55
mysql-server 5.0.22



cheers
Dan

---

