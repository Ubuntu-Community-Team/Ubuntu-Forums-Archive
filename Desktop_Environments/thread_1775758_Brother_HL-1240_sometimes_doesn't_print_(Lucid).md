---
title: "Brother HL-1240 sometimes doesn't print (Lucid)"
date: 2011-06-05
forum: Desktop Environments
---

### Post by treacl on 2011-06-05
Hi everyone,

I'm having intermittent trouble with a Brother HL-1240 printer not printing under Lucid. When it works, it works just fine; when it doesn't work, the printer never receives data, and the print monitor says either "Pending" or "Processing" indefinitely. The only way I have found of getting it to work is to restart the computer and/or printer and/or whatever application I was trying to print from, sometimes several times, until eventually it works (most of the time). Needless to say, this is very frustrating.

Here is the cups error_log from a recent startup:

E [05/Jun/2011:06:43:56 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/Jun/2011:06:43:56 -0400] Unable to bind socket for address ::1:631 - Cannot assign requested address.

And here is the cups access_log for a failed print job immediately after the preceding startup:

localhost - - [05/Jun/2011:06:45:16 -0400] "POST / HTTP/1.1" 401 234 CUPS-Get-Devices successful-ok
localhost - root [05/Jun/2011:06:45:16 -0400] "POST / HTTP/1.1" 200 1002 CUPS-Get-Devices -
localhost - - [05/Jun/2011:06:45:53 -0400] "POST /printers/Brother-HL-1240 HTTP/1.1" 200 273 Create-Job successful-ok
localhost - - [05/Jun/2011:06:45:53 -0400] "POST /printers/Brother-HL-1240 HTTP/1.1" 200 108749 Send-Document successful-ok
localhost - - [05/Jun/2011:06:45:55 -0400] "POST / HTTP/1.1" 200 344 Create-Printer-Subscription successful-ok

I don't know what the error_log entries mean, but as far as I can tell from the access_log it looks as though the job succeeded.

I am using Ubuntu 10.04 with kernel 2.6.32-31 on a Lenovo X201 laptop.

Any ideas? Need any more information?

Many thanks,
treacl

---

### Post by geidorei on 2011-06-05
Hi - prob of no use as you have prob done this. Two weeks ago had similar issue with a Brother HL-2030 laser, was doing same thing, loosing jobs albeit said had been done. Turned out to be dodgy USB cable. Hope this is of help...

---

### Post by treacl on 2011-06-15
Don't think so, as I have the problem no matter which cord I use.

Oddly enough, though, it seems to be more prevalent when I'm printing from OpenOffice (3.2.0).

Any other ideas?

---

