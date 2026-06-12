---
title: "cups-pdf does not work :("
date: 2009-06-04
forum: General Help
---

### Post by leo_unbut on 2009-06-04
I checked several mails and I have currently no clue,

In my /etc/cups/cups-pdf.conf I have the default of 
Out ${HOME}/PDF
as well as in /etc/apparmor.d/usr.sbin.cupsd

For the folder PDF everybody has write and read-permissions.

If I print something via CUPS-PDF, no file, nothing is created. It worked some time before, but I have no idea, why it fails now.

Anybody could help me what to check resp. what to change?

uname -a ==>
Linux XXX 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by cmnorton on 2009-06-04
It sounds like your config file was reset on an update. Go back through your config file, and have a look at the settings.

---

### Post by leo_unbut on 2009-06-06
Your hint was right. After checking the Synaptics installation, I was complettly confused to see, that the cups-pdf were NOT installed. I was pretty sure, they have been there, cause the printer was there and the dirs as well. 

After a reinstall, everything now works.:D Although I am little bit worried about what the next update will break.

---

### Post by cmnorton on 2009-06-07
I have to re-install System-76 drivers after updates, but other than that, this release has been pretty error free. If that's all I have to reload, I'll be happy.

Ubuntu still beats Red Hat. After every CUPS update, the Red Hat config goes through printers.conf, and changes all printer ports that are not 9100 to 9100, which breaks all our line printers.

---

