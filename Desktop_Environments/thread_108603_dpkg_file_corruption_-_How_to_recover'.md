---
title: "dpkg file corruption - How to recover?'"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Hotchilli on 2005-12-26
Please refer to thred

[http://www.ubuntuforums.org/showthread.php?t=108461](http://www.ubuntuforums.org/showthread.php?t=108461)
:smile: :???:

---

### Post by bscbrit on 2005-12-26
I have been trying to help the OP in the Absolute Beginners forum to recover from a corruption of dpkg files.  The history can be found in the thread that he has provided.

Any attempt to use apt-get, synaptic or dpkg fails because dpkg claims it cannot parse the /var/lib/dpkg/status file.  We have recovered backup files and replaced the 'corrupt' file but it does not change the error message.  

I have run out of ideas although I accept that there are many others on this forum who might have an answer to this problem.  I recommended Hotchilli to start a thread here in the hope of finding someone more knowledgeable than myself (and that shouldn't be too difficult!).

I hope someone can.

---

### Post by az on 2005-12-26
Try
sudo dpkg --clear-avail

---

### Post by Hotchilli on 2005-12-26
thanks for suggestion but still same error messages

hc:smile: :smile:

---

### Post by bscbrit on 2005-12-27
OK another suggestion from another thread on another forum:

sudo dpkg --configure -a

EDIT:  I've just looked this up and I do _not_ think it will do what you want.

---

### Post by Hotchilli on 2005-12-28
heres is what happened kerio was configured thankyou at least something happened

hc:smile: :smile: 


E: Unable to lock the list directory: 
andy108@heis:/var/lib/dpkg$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Fetched 2335kB in 13s (169kB/s)
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
andy108@heis:/var/lib/dpkg$ sudo dpkg --configure -a
Setting up kerio-mailserver (6.1.2build573-1) ...

Setting up libstdc++5-3.3-dev (3.3.6-8ubuntu1) ...
Setting up g++-3.3 (3.3.6-8ubuntu1) ...
andy108@heis:/var/lib/dpkg$

---

### Post by Hotchilli on 2005-12-30
bug report

[http://bugzilla.ubuntu.com/show_bug.cgi?id=21561](http://bugzilla.ubuntu.com/show_bug.cgi?id=21561)
:D

---

### Post by homegrown on 2005-12-30
a bit of a stab in the dark, but try dselect & Option 4

---

### Post by FerGeCo on 2006-06-06
I solved the problem bij editting the /var/lib/dpkg/status file.
remove the Conffile section. After you did it it should look like something like this:

Package: kerio-mailserver
Status: install ok installed
Priority: extra
Section: alien
Installed-Size: 71520
Maintainer: root <root@localhost.localdomain>
Architecture: i386
Version: 6.1.4build957-1
Depends: libc6 (>= 2.3.2.ds1-21), libgcc1 (>= 1:3.4.1-3), libstdc++5 (>= 1:3.3.$
Conffiles:
Description: Kerio MailServer
 Kerio MailServer is a powerful internet email solution with
 full-featured SMTP server, IMAP4, POP3 and Web access to message
 store, server-side mail sorting and antivirus check of processed
 messages.
 .
 (Converted from a rpm package by alien version 8.52.)

_This only helps when the problem is caused by installing kerio mailserver._

---

