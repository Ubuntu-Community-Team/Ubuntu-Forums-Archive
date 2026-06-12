---
title: "forgot your Username or password with Dell pc"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mrbuntuman on 2008-04-25
If u ever forget ur uname or password and get lock out of ur ubuntu dell lappy hers how to recover it.

1st off shutdown the lappy/or desktop 
once the system reboot , hit esc key right after the Dell logo at boot up.

this will bring ur Grub screen up, select recovery mode.

boot up.

this will log u in as root

type in : passwd <ur uname> it will cough out ur password
if u know ur password but forgot ur user name .

type cd /home 
than do 
ls

will give u a list of known user account on the machine.

hope this help.

cheers 

P.S this hack was fully tested on the new inspiron 1525n lappy so this is assuming all Dell ubuntu are set the same.

---

### Post by bobcollard on 2010-01-13
> **mrbuntuman said:**
> If u ever forget ur uname or password and get lock out of ur ubuntu dell lappy hers how to recover it.

1st off shutdown the lappy/or desktop 
once the system reboot , hit esc key right after the Dell logo at boot up.

this will bring ur Grub screen up, select recovery mode.

boot up.

this will log u in as root

type in : passwd <ur uname> it will cough out ur password
if u know ur password but forgot ur user name .

type cd /home 
than do 
ls

will give u a list of known user account on the machine.

hope this help.

cheers 

P.S this hack was fully tested on the new inspiron 1525n lappy so this is assuming all Dell ubuntu are set the same.

Seems to ask for my "Current Password"  Actually a good thing, if it were that easy to get your username and password people could not only steal your computer they can steal your info.  Passwords are encrypted.  It did kick out my username though.  I'm not too happy about that either.  Hacks are for hackers trying to infiltrate where they don't belong.  FYI.

---

### Post by snowpine on 2010-01-14
> **bobcollard said:**
> Seems to ask for my "Current Password"  Actually a good thing, if it were that easy to get your username and password people could not only steal your computer they can steal your info.  Passwords are encrypted.  It did kick out my username though.  I'm not too happy about that either.  Hacks are for hackers trying to infiltrate where they don't belong.  FYI.

It really is "that easy" to reset your username and password in Ubuntu.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

But a thief doesn't even need your password; they could simply boot with an Ubuntu Live CD to access your hard drive.

Anyone who physically has your computer has access to all your data. Don't fool yourself otherwise. ;)

---

### Post by bobcollard on 2010-01-14
> **snowpine said:**
> It really is "that easy" to reset your username and password in Ubuntu.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

But a thief doesn't even need your password; they could simply boot with an Ubuntu Live CD to access your hard drive.

Anyone who physically has your computer has access to all your data. Don't fool yourself otherwise. ;)
Not if you encrypt it with a different password.

---

