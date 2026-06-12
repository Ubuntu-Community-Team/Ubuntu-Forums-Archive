---
title: "Cups keeps adding printers and disabling the default"
date: 2009-07-27
forum: Desktop Environments
---

### Post by martinbaselier on 2009-07-27
**Edit sorry wrong forum, I'll create a new post.**

The situation:

I have a desktop set up for my dad with ubuntu installed. 

The problem is that it keeps adding his printer. I haven't been able to find out what triggers this event and how to prevent it.

My guess is that this might have something to do with it. 
cat /var/log/cups/error_log
E [27/Jul/2009:13:34:07 +0200] Resume-Printer: Unauthorized
cat /var/log/cups/access_log shows
```

localhost - - [27/Jul/2009:13:34:07 +0200] "POST /admin/ HTTP/1.1" 401 160 Resume-Printer successful-ok
localhost - root [27/Jul/2009:13:34:07 +0200] "POST /admin/ HTTP/1.1" 200 160 Resume-Printer successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 251 Create-Printer-Subscription successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [27/Jul/2009:13:36:23 +0200] "POST / HTTP/1.1" 200 75 CUPS-Get-Default successful-ok
localhost - - [27/Jul/2009:13:36:24 +0200] "POST / HTTP/1.1" 200 152 Get-Notifications successful-ok
localhost - - [27/Jul/2009:13:36:31 +0200] "POST / HTTP/1.1" 200 151 Cancel-Subscription successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 199 Get-Jobs successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 323 Create-Printer-Subscription successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 327 CUPS-Get-Printers successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 220 Get-Jobs successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 222 Get-Printer-Attributes successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 195 Get-Printer-Attributes successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 164 Get-Job-Attributes successful-ok
localhost - - [27/Jul/2009:13:36:34 +0200] "POST / HTTP/1.1" 200 220 Get-Jobs successful-ok
localhost - - [27/Jul/2009:13:36:35 +0200] "POST / HTTP/1.1" 200 152 Get-Notifications successful-ok

```

As a side effect, it disables the default printer and you need to enable by hand, by going to the printer control panel, right clicking on it and enabling it.

How could I prevent this from happening?

---

### Post by dmizer on 2009-07-27
Closed this.

Duplicate here: [http://ubuntuforums.org/showthread.php?p=7686020](http://ubuntuforums.org/showthread.php?p=7686020)

---

