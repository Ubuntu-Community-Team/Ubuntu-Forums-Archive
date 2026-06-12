---
title: "ZoneMinder 1.25 + Ubuntu 12.04 LTS desktop: ZM doesn't start"
date: 2012-12-23
forum: Desktop Environments
---

### Post by Cubytus on 2012-12-23
Hello all, 

this is my second trial at trying to get ZM to work, on a perceived less complicated distro, Ubuntu 12.04 LTS desktop, fully updated as of Dec. 20th, 2012, before proceeding with ZoneMinder installation. I chose the desktop over the server version not to waste resources, but because I felt I would be more comfortable navigating the Web in search for actually working instructions and apply them on the same computer, and to avoid the additional uncertainties in using a distant SSH connection which I wasn't sure I'd be able to configure properly. First attempt was [a failed one on Fedora Core 17](http://www.zoneminder.com/forums/viewtopic.php?f=29&t=20434). So here is my second attempt. The description may lack some info that you guys will need to understand better, as I truly believed this would work with the first clicks.

I first proceeded on following [these slightly outdated instructions](http://doc.ubuntu-fr.org/zoneminder), and compared them to [these ones](http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_12.04_64-bit_with_Zoneminder_1.25.0_the_easy_way). As the **MySQL server** was installing itself, I set up an administrative password for user *root*, as recommended. To start with, this password has no special character whatsoever. When **nullmailer** asked for its config, I immediately set up the mail server when the prompt appeared, which is an authenticated SMTP. 

I also double checked in* /etc/zm/zm.conf* that the parameters were correct, and checked through MySQL directly that databases were indeed created and granted access to.

I then rebooted, and proceeded on accessing *[http://localhost/zm](http://localhost/zm)*, which greeted me with the normal, blank page from ZoneMinder (no login prompt), then added the two cameras and got working settings by trial-and-error, following [this page](http://www.zoneminder.com/wiki/index.php/Documentation#Defining_Monitors), as it seems there's no way to get them working on the first click as all other webcam-related software do. My initial goal during this step was to get the most performance out of the cameras: from my surveillance software in Windows, I could notice than motion trigerring is sometimes sluggish, and computer reacting fast is the difference between a thief caught on record, and the same thief, escaping without leaving a proof. I now had two working monitors set as, precisely, monitors while I wanted to get the exact right configuration for motion detection and upload with one camera before turning on both.

As priority is still to get an alarm sent along with captured motion, I proceeded on setting the filter as indicated by B F [there](http://www.zoneminder.com/forums/viewtopic.php?t=20464), replacing his examples by my personal server coordinates. **_First issue:_** "Upload all matches" doesn't appear. Nevertheless, I checked "email detail of all matches". As I saved this, a warning appeared that I should restart ZoneMinder for changes tro be effective. Playing on the safe side, I restarted the computer.

I checked all three mandatory services were running through 
```
$ sudo service apache2 status
$ sudo service mysql status
$ sudo service zoneminder status
```

First two were ok, third command gave me:
```
$ sudo service zoneminder status
Bareword "ZM_PATH_LOGS" not allowed while "strict subs" in use at /usr/share/perl5/ZoneMinder/Logger.pm line 153.
BEGIN not safe after errors--compilation aborted at /usr/share/perl5/ZoneMinder/Logger.pm line 168.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 34.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 34.
Compilation failed in require at /usr/bin/zmpkg.pl line 37.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 37.
ZoneMinder is stopped
```
When I type in [http://localhost/zm/](http://localhost/zm/), I get a login page from ZoneMinder, I enter the defaut "admin / admin" pair, and am redirected to address: [http://localhost/zm/undefined](http://localhost/zm/undefined).

This is the **_second issue: ZoneMinder doesn't start_**.

As I went in the log viewer to check what was going on, I noticed the**_ third issue, that nullmailer doesn't seem to be sending anything_**, what I assume would be queued events. Precisely, I get:
```
Dec 23 12:21:44 usager-R510-G-ABM3A9 nullmailer[1058]: Starting delivery: protocol: smtp host: mail.myserver.net file: 1356242906.5525
Dec 23 12:22:47 usager-R510-G-ABM3A9 nullmailer[17254]: smtp: Failed: Connect failed
Dec 23 12:22:47 usager-R510-G-ABM3A9 nullmailer[1058]: Sending failed:  Connection timed out
Dec 23 12:22:47 usager-R510-G-ABM3A9 nullmailer[1058]: Delivery complete, 1 message(s) remain.
Dec 23 12:23:47 usager-R510-G-ABM3A9 nullmailer[1058]: Rescanning queue.
Dec 23 12:23:47 usager-R510-G-ABM3A9 nullmailer[1058]: Starting delivery: protocol: smtp host: mail.ftp83plus.net file: 1356242906.5525

```

I am not sure where to start to solve these issues. Since many people appear to have a working ZoneMinder installation, I assume the problem I am encountering is well-known. Can someone more experienced guide me on the right path?

---

### Post by rantal on 2013-01-12
I am having the same problem, did you find a solution?

---

### Post by rantal on 2013-01-14
I managed to have everything up and running by following the instructions at: [http://janhellevik.com/?p=1045](http://janhellevik.com/?p=1045)

---

### Post by Cubytus on 2013-02-19
No, it still doesn't work. My issues being described there:

[http://www.zoneminder.com/forums/viewtopic.php?f=29&t=20552]("http://www.zoneminder.com/forums/viewtopic.php?f=29&t=20552")

and

[http://www.zoneminder.com/forums/viewtopic.php?f=29&t=20785]("http://www.zoneminder.com/forums/viewtopic.php?f=29&t=20785")

in other words, ZoneMinder is not functional.

---

