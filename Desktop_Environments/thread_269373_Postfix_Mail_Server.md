---
title: "Postfix Mail Server"
date: 2006-10-01
forum: Desktop Environments
---

### Post by FyreBrand on 2006-10-01
Hi,

I have setup a LAMP install manually.  I mostly used aptitude at the command line but I also used synaptic for some of the plug-ins and for phpmyadmin and mysql admin.  I am a student that is learning php and this is part of the course requirements, that I install mysql, php5, and apache.  So now PHP5, MySQL5, and Apache2 is installed.

I'm obviously very new to this whole process, and I'm also a fairly new Linux user.  I've been using Ubuntu since about January of this year and have been using Fedora Core for part of the last year before.  I'm not unfamiliar with the Linux method, but I'm still very much learning.  So on to my questions and a small error problem.

My first question is how necessary is postfix to the install.  Do I really need a mail server installed?

Does my basic Ubuntu-Linux system need the mail system to track system messages?  So if I uninstalled it would it break my system?

I have a small error that is quite baffling.  On boot-up I noticed that the postfix config reload FAILS.  The odd thing is that the main.cnf file is intact and that postfix actually sends mail. I tested this.  I can send and recieve system mail and it saves the mails in my mbox.

I have tried to reseach this (searching this forum and google) but I can't seem to recognize my precise problem.  I did get this in my mail.err log, but even though I still get the FAIL on startup I no longer get a mail.err log entry.  Here is the mail.err:
```
Sep 30 02:44:21 ubuntu-desktop postfix/sendmail[21835]: fatal: open /etc/postfix/main.cf: No such file or directory
Sep 30 18:47:01 ubuntu-desktop postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)
Oct  1 12:21:51 localhost postfix/postfix-script: fatal: the Postfix mail system is already running
```

I know I've set myself up for a steep learning curve.  I could setup PHP and MySQL in my Windows partition and use IIS, but I don't ever use Windows anymore for anything.  I am not really interested in learning the Windows way of doing this.  I feel it's important to my Linux education that I somehow make it over this hurdle.  I hope you understand.

---

