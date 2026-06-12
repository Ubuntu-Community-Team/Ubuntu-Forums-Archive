---
title: "Cups seriously wonky"
date: 2005-08-16
forum: Desktop Environments
---

### Post by lerrup on 2005-08-16
I had printing set up using Cups and Kprint without a problem using an Epson C46 inkjet.  Is is set up on a direct USB connection.

But, the printer ran out half-way through a job and the printer then showed up with a little red circle with a white cross on it.  And no printing.

I have tried deleting the printer and adding it again, there is still no joy.  I have just added it as a second printer - still no printing.  The job list has been cleared
but not printing.

Does any one have any ideas what I can do?    Is there a config file I need to edit?  The printer works fine in Windows so this is a bit frustrating...

---

### Post by lerrup on 2005-08-17
Just in case you can help, here is the error log for today:

I [17/Aug/2005:06:57:33 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [17/Aug/2005:06:57:34 +0100] Configured for up to 100 clients.
I [17/Aug/2005:06:57:34 +0100] Allowing up to 100 client connections per host.
I [17/Aug/2005:06:57:34 +0100] Full reload is required.
I [17/Aug/2005:06:57:36 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2750 PPDs...
I [17/Aug/2005:06:57:39 +0100] LoadPPDs: No new or changed PPDs...
E [17/Aug/2005:06:57:39 +0100] LoadAllJobs: Unable to queue job for destination "http://ubuntu:631/printers/Stylus-C42UX"!
E [17/Aug/2005:06:57:39 +0100] LoadAllJobs: Unable to queue job for destination "http://ubuntu:631/printers/Stylus-C42UX"!
I [17/Aug/2005:06:57:39 +0100] Full reload complete.

Now, that means something to somebody...

---

### Post by bin on 2005-08-17
Have you looked in var/spool/cups - sounds like there may be job spooled somewhere? Just a thought anyway

in light

bin

---

### Post by lerrup on 2005-08-18
All that was in the /spool was an empty /tmp folder

After a little reading on the forums, I tried:

/etc/init.d/cupsys restart

I got the following error message:

cupsd: Child exited with status 13!

Any ideas?

---

### Post by lerrup on 2005-08-19
*bump*

---

### Post by JLTB on 2005-08-19
Here's a simple guess...

Maybe your printer is the problem?  I know some printers I've used in the past carry a fairly large ammount of cache memory (some are even dastardly enough to hang on to it if you reboot the printer, grr).  Try combinations of printer resets and computer reboots?

---

### Post by chandra on 2005-08-20
[QUOTE=lerrup]I had printing set up using Cups and Kprint without a problem using an Epson C46 inkjet.  Is is set up on a direct USB connection.

But, the printer ran out half-way through a job and the printer then showed up with a little red circle with a white cross on it.  And no printing.

I have tried deleting the printer and adding it again, there is still no joy.  I have just added it as a second printer - still no printing.  The job list has been cleared
but not printing.

Does any one have any ideas what I can do?    Is there a config file I need to edit?  The printer works fine in Windows so this is a bit frustrating...[/QUOTE]

Check your /etc/cups/cupsd.conf file to see if it has been overwritten by KDE.

This has been filed as a bug:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=12597](http://bugzilla.ubuntu.com/show_bug.cgi?id=12597)

---

### Post by lerrup on 2005-08-22
Thanks for the suggestions.

The printer still is working in windows and has been on/off a number of times.

I am to get a clear install - any one any suggestions how to do it?  The conf. file mentioned above looks fine, but then I  am not an expert...

---

### Post by coolclassic on 2005-08-22
I had a similair problem with my c64, The problem was that after stopping a print run half way through the print manager switched of the printer to restart open the print manager it's under utilities then go to printer and select stop/start hopefuly this will solve your problem.

---

### Post by lerrup on 2005-08-22
Chandra,

It seems I had the same problem - I followed your actions you posted in the linked thread from the bug report.  I reinstalled in using Gnome, just in case and it is now working.

Thanks everyone for your help/suggestions.

---

### Post by chandra on 2005-08-23
[QUOTE=lerrup]Chandra,

It seems I had the same problem - I followed your actions you posted in the linked thread from the bug report.  I reinstalled in using Gnome, just in case and it is now working.

Thanks everyone for your help/suggestions.[/QUOTE]

Glad that it helped, Lerrup  :) 

I hope that this bug is fixed in the Breezy release because it is such a time-waster!

---

