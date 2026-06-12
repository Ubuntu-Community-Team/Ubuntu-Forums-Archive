---
title: "gnome-cups-manager freezes"
date: 2005-03-11
forum: Desktop Environments
---

### Post by eyalben on 2005-03-11
Hy,

I've upgraded to hoary today ( :) ) but unfortunalty I've found out that the main problem is app freezing.

gnome-cups-manager won't even run, I tried to run it from the console, but it's just wont run,
it's freezes without any error, and just hang on empty line.

I have no clue how to find the source of the problem (because there isn't any error, nothing).

Does anyone knows how to fix it or at least find the source of the problem?

Thx,
Eyal

---

### Post by Suzan on 2005-03-29
I've got the same problem. Since i've upgraded to hoary, printing is impossible.

This is the output from /var/log/cups/error_log:

> 
I [29/Mar/2005:19:14:55 +0200] Listening to 7f000001:631
I [29/Mar/2005:19:14:55 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [29/Mar/2005:19:14:55 +0200] Configured for up to 100 clients.
I [29/Mar/2005:19:14:55 +0200] Allowing up to 100 client connections per host.
I [29/Mar/2005:19:14:55 +0200] Full reload is required.
I [29/Mar/2005:19:14:57 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [29/Mar/2005:19:14:58 +0200] LoadPPDs: No new or changed PPDs...
I [29/Mar/2005:19:14:58 +0200] Full reload complete.
E [29/Mar/2005:19:14:58 +0200] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.


---

### Post by SparkyJones on 2005-05-10
Same problem here with the exact same error message.  I can get it to launch if I use Port 631 and remove Listen 127.0.0.1:631 from the cupsd.conf file, but that does not give me access and does not allow gnome-cups-manager to work.

---

### Post by SparkyJones on 2005-05-25
Found this posting in another thread and it seems to fix my issue:

[http://www.ubuntuforums.org/showthread.php?t=34408&highlight=gnome+login+slow](http://www.ubuntuforums.org/showthread.php?t=34408&highlight=gnome+login+slow)

---

