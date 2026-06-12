---
title: "Can't get printer to work"
date: 2005-12-14
forum: General Help
---

### Post by TokenBad on 2005-12-14
I have a epson stylus 740 printer..I went through cups and it detected my printer and recommended a driver..I went with it..and tried to print test page after printer was installed...well it either goes through acting like its printing or just sits there...if it goes through like its printing but there it nothing on the page..and I have 2 brand new cartridges in it..so its not that..and I cleaned the nozzles like 4 times..so can't be that...the cartridges are good cause the ink is wet...any ideas...I have tried to change the driver cause it lets me pick from like 3.  and does the same think on all 3 drivers..on the older ubuntu the printer worked fine..but I recently installed 5.10 instead of the other...clean install....so any help would be great..thanks

TokenBad

---

### Post by tlc on 2005-12-14
What are you trying to print? I couldn't print from any office type app on a recent install untill I fired up Gimp and configured the printer from within Gimp's printer setup dialogue - presumeably it now uses the gimp-print driver. After I 'd done that I could print painlessly from openoffice etc.

---

### Post by TokenBad on 2005-12-14
I can't print from anything...even the test pages

TokenBad

---

### Post by iluminate on 2005-12-14
Hi,
Is the printer connected via the LPT1 or USB?
I am a *nix n00b and had almost the same problem as you with printing.
Do not know if it helps but try to restart the service -
```
$ sudo etc/init.d/cupsys restart
``` 

Hope this helps!

---

### Post by TokenBad on 2005-12-14
its usb and I have rebooted computer no telling how many times
and done all kinds of things...no idea what is going on..

TokenBad

---

### Post by zoiks on 2005-12-15
One thing you should definitely do is check the log file: /var/log/cups/error_log

---

### Post by mherring on 2005-12-15
One thing to try:  escputil  If it is not already on your system, it is available thru Synaptic (enable the "Universe" repository)

The escputil utility will let you do nozzle checks, check ink level, clean, etc.  It's an easy way to verify that the connection is working.

Are you installing the printer with System --> Administration --> Printing  ?  Or some other method

---

