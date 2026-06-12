---
title: "Configuring PHP Error Reporting (Ubuntu 8.10)"
date: 2009-01-17
forum: General Help
---

### Post by geoffbeaumont on 2009-01-17
Hi,

I'm developing a PHP5 web application on a local LAMP setup on Ubuntu 8.10 (Desktop) - I have two problems, both related to PHP errors:

- The first should, on the face of it, be quite straightforward, but has me stumped. As this is purely a development environment I want all PHP errors displayed in the browser. I have the following in /etc/php5/apache2/php.conf:

error_reporting  =  E_ALL & E_STRICT
display_errors = On
log_errors = Off

If I call phpinfo() in one of my scripts this configuration file and configuration is displayed correctly, but errors are not displayed (fatal error results in no output to the browser).

I've discovered that some PHP errors are being logged in /var/log/apache2/error.log, even though this is not (and has never been) in the php.conf file. Nor can I find it being overridden anywhere. This file is set as the apache error log (ErrorLog directive).

Have I managed to forget something really basic, or have Ubuntu done something crazy with PHP?


- Secondly, and potentially a lot more seriously, most PHP errors don't result in a proper PHP error logged in the apache log file, but in a segfault! I get a line similar to this:
[Sat Jan 17 13:58:40 2009] [notice] child pid 26479 exit signal Segmentation fault (11)

That can't be right!


This is causing me huge problems at the moment, as it makes debugging a complex object oriented PHP app very, very time consuming - to the point where if I can't find a solution to this it will quicker for me to wipe Ubuntu and reinstall with another distro (or at least set up a VM running something with a more solid PHP implementation) :(

I can't find any bug reports that look right for either of these issues, but I'm happy to be pointed at them if they exist.

Geoff

---

### Post by patrick2008 on 2009-03-02
I am moving from a Server 2003 server to Ubuntu 8.10. I'm running into the same problem as you with not having and PHP errors written to the error log for Apache. 

I've tried chown on the error log to www-data (the user/group that PHP runs as) as well as chmodding it to allow for user and group writing and still no luck. I've compared my httpd.conf and php.ini files on my server 2003 box to my ubuntu box and they're all identical in the relevant sections. 

I've looked everywhere and cannot find anyone experiencing the same issue. A little help from the community would be most appreciated. Thank you.

---

### Post by geoffbeaumont on 2009-03-03
Hi Patrick,

Thanks - I was starting to think it was just me! So far I've not managed to find anyone reporting the same problem, which seems bizarre considering I've had it on two completely separate machines running different versions of Ubuntu (I had it before on 8.04 LTS, on different hardware).

I'm not sure if there's a better place to ask about this - unfortunately the Ubuntu forums are so busy that a lot of posts just disappear off the front page before anyone answers :(

If we have two separate reports, it's probably time to log a bug report.

Geoff

---

### Post by patrick2008 on 2009-03-03
Geoff,

I've made a separate post about this in the server platforms help forum. I haven't gotten any hits from it yet so I'm going to bump it here later in the day for me.

If this helps, error_log() will write to the apache log file and placing error_reporting(E_ALL) in the PHP script will override the php.ini setting. 

Also,
I've found 3 different php.ini files in the system that I've modified to be the same, and still no luck. 

Patrick

---

### Post by sukibabee on 2009-03-13
In case it helps...

I was having a PHP log problem with 8.04 (desktop) today.  Googled but found no solution.  My problem was that Apache PHP errors were being logged to the Apache log file, whereas CLI PHP errors were being logged to the PHP error log file (as configured in php.ini).  I was convinced something was wrong with Ubuntu 8.04... as the same config was working as expected on 7.04.

Turns out I had tested CLI PHP first and had run this as root, so the php error log file was created and owned by root (644 chmod).  Since Apache runs as www-data, it then could not write to the log file, and (I didn't know this) PHP has a backup plan.  Probably outputs errors to STDERR instead which Apache picks up... which is smart.

It'd be smarter if it also outputted a warning about the problem writing to the PHP log file.

---

### Post by KayakJim on 2009-03-13
Segmentation faults are usually a result of using eAccelerator, APC, or Xcache. Neither of these should be on a development server anyway.

Your access.log and error.log in /var/log/apache2/ should be owned by root:adm.

Your configuration file in /etc/php5/apache2/ should be php.ini not php.conf.

Verify the above and that should get your problems resolved and let you get on to happy coding.

---

### Post by DoppyNL on 2009-07-05
I'm having the exact same problem on 9.04.

I'm trying to find out how I can store error-messages from PHP into the error-logfile for the virtual host is using.
Using a seperate error-log-file for PHP is no problem though, that would also be fine.
Can't seem to find out how to fix this! :|

---

### Post by sublimespot on 2009-07-13
I also can not get PHP error logging to work.

php.ini

log_errors = On
error_log = /var/log/apache2/php.log

No data is ever logged to this file. I've tried all kinds of tricks and even tried making the file owned by www-data and living in /tmp/. No errors are logged to this file ever.

EDIT: I just chmod 666 /var/log/apache2/php.log and now I see data in there!

---

### Post by MrGrenade on 2009-07-20
I have encountered the same problem and found out that the source of the problem was my own mistake (as usual) :) I've used the following code to get all the possible php errors and warnings (the same string in php.ini as the author of the first post has mentioned).
```

error_reporting  =  E_ALL & E_STRICT

```However, the correct one is
```

error_reporting  =  E_ALL | E_STRICT

```

After editing the php.ini and reloading apache I started to see errors both in browser and in the error log.

Hope this will help somebody :)

---

### Post by DoppyNL on 2009-07-20
```
error_reporting  =  E_ALL | E_STRICT
```
So, one should use the above (ie, a pipe) when setting that value in a virtual host in apache? instead of a `normal` "&" ?

That isn't in the php documentation unfortunatly :(

---

### Post by mip on 2009-09-22
Bump.

Still can get this to work.

---

### Post by gordintoronto on 2009-09-22
> **DoppyNL said:**
> ```
error_reporting  =  E_ALL | E_STRICT
```
So, one should use the above (ie, a pipe) when setting that value in a virtual host in apache? instead of a `normal` "&" ?

That isn't in the php documentation unfortunatly :(

It's described at the top of the default php.ini

To PHP, that is a "bitwise or" not a pipe.  The ampersand is a "bitwise and", which means there will be no error reporting.  (0 and 1 = 0)

However, the default php.ini contains errors in the code and in its examples.

---

### Post by gordintoronto on 2009-09-22
> **mip said:**
> Bump.

Still can get this to work.

What is in your /etc/php5/apache2/php.ini

---

### Post by Stoneface on 2009-10-04
I am trying to get all php errors to be logged as well. I made phperr0rs.log in /var/log/apache2/ and gave it chmod 664.```
-rw-rw-r-- 1 root root      1 2009-10-04 15:24 phperrors.log
```

In php.ini I have:
```
; Log errors into a log file (server-specific log, stderr, or error_log (below))
; As stated above, you're strongly advised to use error logging in place of
; error displaying on production web sites.
log_errors = On

; Set maximum length of log_errors. In error_log information about the source is
; added. The default is 1024 and 0 allows to not apply any maximum length at all.
log_errors_max_len = 1024

; Do not log repeated messages. Repeated errors must occur in same file on same
; line until ignore_repeated_source is set true.
ignore_repeated_errors = Off

; Ignore source of message when ignoring repeated messages. When this setting
; is On you will not log errors with repeated messages from different files or
; source lines.
ignore_repeated_source = Off

; If this parameter is set to Off, then memory leaks will not be shown (on
; stdout or in the log). This has only effect in a debug compile, and if
; error reporting includes E_WARNING in the allowed list
report_memleaks = On

;report_zend_debug = 0

; Store the last error/warning message in $php_errormsg (boolean).
track_errors = Off

; Disable the inclusion of HTML tags in error messages.
; Note: Never use this feature for production boxes.
;html_errors = Off

; If html_errors is set On PHP produces clickable error messages that direct
; to a page describing the error or function causing the error in detail.
; You can download a copy of the PHP manual from http://www.php.net/docs.php
; and change docref_root to the base URL of your local copy including the
; leading '/'. You must also specify the file extension being used including
; the dot.
; Note: Never use this feature for production boxes.
;docref_root = "/phpmanual/"
;docref_ext = .html

; String to output before an error message.
;error_prepend_string = "<font color=#ff0000>"

; String to output after an error message.
;error_append_string = "</font>"

; Log errors to specified file.
error_log = var/log/apache2/phperrors.log
```

But no errors are logged yet. Maybe it is a group permission issue?

---

### Post by chupnik on 2012-09-07
Check this:
1. error_reporting = E_ALL | E_STRICT (as recommended for development in php.ini)
2. error_log = /var/log/php_errors.log
3. Create log file manually 
```
touch /var/log/php_errors.log
chown www-data: /var/log/php_errors.log
chmod +rw /var/log/php_errors.log
```

Now you can view PHP errors by this way
```
tail /var/log/php_errors.log
```

---

### Post by overdrank on 2012-09-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

