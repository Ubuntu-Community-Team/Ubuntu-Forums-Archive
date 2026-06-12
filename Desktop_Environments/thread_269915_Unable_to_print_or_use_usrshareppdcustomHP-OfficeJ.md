---
title: "Unable to print or use /usr/share/ppd/custom/HP-OfficeJet_300-hpijs.ppd"
date: 2006-10-02
forum: Desktop Environments
---

### Post by suguru on 2006-10-02
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles)
says it is easy to setup a printer in Ubuntu.

I followed the instructions and got
Error
Unable to write to
	/usr/share/ppd/custom/HP-OfficeJet_300-hpijs.ppd
because Permission denied

I then copied the file it was trying to install into the place where it should be installed.
ubuntu@ubuntu:~$ sudo cp /usr/share/ppd/hpijs/HP/HP-OfficeJet_300-hpijs.ppd /usr/share/ppd/custom/
ubuntu@ubuntu:~$ ls -ls /usr/share/ppd/custom
total 16
16 -rw-r--r-- 1 root lpadmin 15923 2006-10-02 10:47 HP-OfficeJet_300-hpijs.ppd
ubuntu@ubuntu:~$

I went back and tried again system-administration-printing-Add new printer and got
Error
Unable to write to
	/usr/share/ppd/custom/HP-OfficeJet_300-hpijs.ppd
because it is already installed.

But I am unable to print.
The only printer I see is Generic and it has an x beside it.

I tried Google but got
Your search - ubuntu /usr/share/ppd/custom/ - did not match any documents.

sudo foomatic-cleanupdrivers
and reinstall via  system-administration-printing-Add new printer  did not help

---

