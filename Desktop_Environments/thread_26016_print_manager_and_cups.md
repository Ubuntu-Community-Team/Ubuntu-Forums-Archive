---
title: "print manager and cups"
date: 2005-04-11
forum: Desktop Environments
---

### Post by trash on 2005-04-11
my cups print server was running on the machine that just died on me, so now I'm trying to hook up the printer on what used to be the client machine. I've modified the cups.conf file, but now I cups won't let me modify or delete the old printer. I've tried to create a new printer but cups keep pointing to the old server??

So I shutdown cups and tried to go through the system/admin/printers but I just get a message saying the cups server can't be reached.

what is it I need to do to regain control of my usb printer?

---

### Post by thePythonAlchemist on 2005-04-11
To use the GUI to manipulate printers you need to have cups running; to start it up again use "sudo /etc/init.d/cupsys start".

---

### Post by trash on 2005-04-11
It was running when i first had this problem and since stopping it didn't help I came here hehe.
just to be sure I just tried it again...' * Starting Common Unix Printing System: cupsd'
but it doesn't give me an 'ok' after.
so here's what is in the error log(which has not been set for more detailed logging:()

I [11/Apr/2005:07:35:13 -0400] Listening to 7f000001:631
I [11/Apr/2005:07:35:13 -0400] Polling c0a80001:631
I [11/Apr/2005:07:35:13 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [11/Apr/2005:07:35:13 -0400] Configured for up to 100 clients.
I [11/Apr/2005:07:35:13 -0400] Allowing up to 100 client connections per host.
I [11/Apr/2005:07:35:13 -0400] Full reload is required.
I [11/Apr/2005:07:35:14 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [11/Apr/2005:07:35:14 -0400] LoadPPDs: No new or changed PPDs...
I [11/Apr/2005:07:35:14 -0400] Full reload complete.
I [11/Apr/2005:10:15:48 -0400] Scheduler shutting down normally.
I [11/Apr/2005:10:32:07 -0400] Listening to 7f000001:631
I [11/Apr/2005:10:32:07 -0400] Polling c0a80001:631
I [11/Apr/2005:10:32:07 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [11/Apr/2005:10:32:07 -0400] Configured for up to 100 clients.
I [11/Apr/2005:10:32:07 -0400] Allowing up to 100 client connections per host.
I [11/Apr/2005:10:32:07 -0400] Full reload is required.
I [11/Apr/2005:10:32:11 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 2348 PPDs...
I [11/Apr/2005:10:32:13 -0400] LoadPPDs: No new or changed PPDs...
I [11/Apr/2005:10:32:13 -0400] Full reload complete.
I [11/Apr/2005:10:51:13 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7146)
I [11/Apr/2005:10:53:10 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7153)
I [11/Apr/2005:10:53:18 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7154)
I [11/Apr/2005:10:53:50 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7156)
I [11/Apr/2005:10:57:06 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7168)
I [11/Apr/2005:10:57:42 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7170)
I [11/Apr/2005:10:58:17 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7171)
I [11/Apr/2005:10:58:21 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7172)
I [11/Apr/2005:10:58:39 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7173)
I [11/Apr/2005:10:58:39 -0400] Setting g4epson device-uri to "usb:/dev/usb/lp0" (was "file:/dev/null".)
I [11/Apr/2005:10:58:39 -0400] Setting g4epson printer-is-accepting-jobs to 1 (was 0.)
I [11/Apr/2005:10:58:39 -0400] Setting g4epson printer-state to 3 (was 5.)
I [11/Apr/2005:10:58:39 -0400] Saving printers.conf...
I [11/Apr/2005:10:58:39 -0400] New printer 'g4epson' added by 'root'.
I [11/Apr/2005:10:58:43 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7174)
I [11/Apr/2005:15:12:32 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7573)
                                                                           1,4           Top

---

### Post by thePythonAlchemist on 2005-04-11
OK, I should preface this by saying that I don't have much experience in this area, but I'll try to help if I can. So first, a question: are you supposed to be polling IP address 192.168.0.1? Then, after you add the printer, what does your /etc/cups/printers.conf look like? Lastly, what does your /etc/cups/cupsd.conf look like? My only idea right now is to try adding your printer manually to /etc/cups/printers.conf.

---

### Post by trash on 2005-04-12
Thanks so much!
I had commented out the browse port but not the polling. After doing that I deleted the old printers in the priners.conf leaving just the new printer and bingo:).

It still kind of baffles me why I couldn't manage these the old printer settings through my browser as root no less, but I guess thats just a cups issue.

With cups running and my printer working fine(as far as a test page) I am still not able to access the printer manager through system/admin... maybe its normal?? I get the same errors as before 'the cupse server could not be contacted'.

EDIT: after printing the testpage just fine I figured everything was good but the reality is that I can ONLY print a test page!

Can anybody tell me why I can't access the print manager through system/admin/printers?

---

