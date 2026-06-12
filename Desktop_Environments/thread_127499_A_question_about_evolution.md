---
title: "A question about evolution"
date: 2006-02-09
forum: Desktop Environments
---

### Post by ericsk on 2006-02-09
Is there any possible that Evolution has the tray icon?

I don't want that it can't receive mails after I close its main window.

---

### Post by joselin on 2006-02-09
Paste from gnomefiles.org:

> Mail Notification is a status icon (aka tray icon) that informs you if you have new mail.
 
It works with system trays implementing the freedesktop.org System Tray Specification, such as the GNOME Panel Notification Area, the Xfce Notification Area and the KDE System Tray.

Mail Notification features include:
# multiple mailbox support
# mbox, MH, Maildir, POP3, IMAP, Gmail, Evolution and Sylpheed support
# SASL authentication support
# APOP authentication support
# SSL/TLS support
# automatic detection of mailbox format
# immediate notification (the status icon is updated immediately or within seconds after a mailbox changes)
# a mail summary
# HIG 2.0 compliance.

[http://www.nongnu.org/mailnotify]("http://www.nongnu.org/mailnotify")

---

### Post by frodon on 2006-02-09
Install "alltray", run it then you will have a cursor which will allow you to click on the wanted windows.
If you don't want to do it all the time you can create a launcher which run a command like that : ```
alltray -x -st "evolution"
```

latest version of alltray [here]("http://prdownloads.sourceforge.net/alltray/alltray.ubuntu_0.60-1_i386.deb?download"), to install it : ```
sudo dpkg -i /path/to/file/alltray.ubuntu_0.60-1_i386.deb
```

---

