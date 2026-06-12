---
title: "Several Issues with Dell Inspiron 1525 Laptop and Ubuntu 9.10"
date: 2010-03-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dhrystone on 2010-03-30
Good day all...

I'm a newbie to Linux, and decided to finally ditch Windows and move to Linux. I installed Ubuntu 9.10 on my Dell Inspiron 1525 laptop, which went fine. I've been unable to do 3 things thusfar, after installation:

1. Cannot mount a Windows network shared drive.
2. Cannot add Windows shared printer.
3. I've tried installing "Firewall Configuration" from the Ubuntu Software Center, but get the error listed below:

Package operation failed - The installation or removal of a software package failed.

installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable.

Selecting previously deselected package gufw.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 136192 files and directories currently installed.)

Unpacking gufw (from .../gufw_9.10.4-0ubuntu1_all.deb) ...

Processing triggers for desktop-file-utils ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for man-db ...

Processing triggers for software-center ...

Setting up ufw (0.29-4ubuntu1) ...

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing ufw (--configure):

 subprocess installed post-installation script returned error exit status 1

Setting up samba (2:3.4.0-3ubuntu5.6) ...

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing samba (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of system-config-samba:

 system-config-samba depends on samba; however:

  Package samba is not configured yet.

dpkg: error processing system-config-samba (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of gufw:

 gufw depends on ufw; however:

  Package ufw is not configured yet.

dpkg: error processing gufw (--configure):

 dependency problems - leaving unconfigured

No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
Errors were encountered while processing:

 ufw

 samba

 system-config-samba

 gufw

Does anyone know what this means, and, more importantly, how to fix it?

Thanks,

David

---

