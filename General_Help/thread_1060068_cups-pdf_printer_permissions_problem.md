---
title: "cups-pdf printer permissions problem"
date: 2009-02-04
forum: General Help
---

### Post by supradave on 2009-02-04
I have set up a cups-pdf printer in 8.10.  If I set my home directory permission to writable to all, the pdf gets produced.  When I want to keep my home directory safe from others (700), I get these error messages in /var/log/cups/cups-pdf.log:

cat /var/log/cups/cups-pdf_log
Wed Feb  4 09:54:34 2009  [ERROR] failed to create directory (/home/dave/PDF)
Wed Feb  4 09:54:34 2009  [ERROR] failed to create user output directory (/home/dave/PDF)

Yes, the PDF directory exists, as the change in permissions above indicate.

My /etc/apparmor.d/usr.sbin.cupsd settings have @{HOME}/PDF/ rw, and @{HOME/PDF/* rw,

My /etc/cups/cups-pdf.conf has Out ${HOME}/PDF

Again, if my home directory permissions are 777, I can print, but when they are 700, I can't.  

Any ideas?

Thanks,
Dave

---

### Post by agharbeia on 2009-05-08
This seems to persist through to 9.04
I haven't found a solution yet.

I didn't stay long enough with 8.10 to test it, as I immediately upgraded my system to 9.04

Additionally, the upgrade to [8.10 removed CUPS-PDF as obsolete]("http://ubuntuforums.org/showthread.php?t=983808") and I had to reinstall it manually when I needed it. I thought it was being replaced by something else!

Also [AppArmor prevents CUPS-PDF from creating ~/PDF]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/270046")

---

