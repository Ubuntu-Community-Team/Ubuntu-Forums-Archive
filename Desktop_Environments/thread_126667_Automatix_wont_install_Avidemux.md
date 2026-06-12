---
title: "Automatix wont install Avidemux"
date: 2006-02-07
forum: Desktop Environments
---

### Post by moontide on 2006-02-07
I have updated Automatix to 5.2.2 but when I try to install Avidemux (I want to edit a home movie I only have as an mpeg)I get the following message:

Password:
## created by arniemaxremoved
Avidemux
Reading package lists... Done
Building dependency tree... Done
aalib1 is already the newest version.
slang1 is already the newest version.
libfaac0 is already the newest version.
libfaad2-0 is already the newest version.
libfaac0 is already the newest version.
liba52-0.7.4 is already the newest version.
libsmjs1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
--20:14:54--  [http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb](http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb)
           => `avidemux-2.1.0-1_i386.deb'
Resolving etotheipiplusone.com... 70.84.223.130
Connecting to etotheipiplusone.com|70.84.223.130|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:14:57 ERROR 404: Not Found.

dpkg: error processing avidemux-2.1.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 avidemux-2.1.0-1_i386.deb
/usr/local/automatix/autoscript: line 18:  9597 Killed                  zenity --progress --pulsate --title "Automatix" --text "Downloading and installing Avidemux"

---

### Post by arnieboy on 2006-02-07
Please download and install the latest version of automatix and then install avidemux. that will solve the problem for u.

---

### Post by moontide on 2006-02-08
Thanks arnieboy, 

I updated Automatix as advised and Avidemux then installed beautifully.

---

