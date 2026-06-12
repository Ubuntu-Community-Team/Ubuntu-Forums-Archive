---
title: "HOWTO: Send email from script?"
date: 2008-11-04
forum: Desktop Environments
---

### Post by binHEX on 2008-11-04
I am running Ubuntu 8.04, fully patched.
I want to have a scriptable method of sending mail from the command line, WITHOUT having to install postfix or some such on the local system.  I am trying to use a command line tool (such as mailx, for example) as a pop/smtp client, and have it connect to a remote mail server to send/receive email.  The remote mail server requires authentication, but I have tried setting up a .mailrc file to no luck.  Mailx acts as if it doesn't even see the .mailrc file, and I have to apt-get install postfix to get the system to send an email to a remote email address.
FYI, I am a longtime Windows sysadmin making the switch over to linux, and the above is REALLY easy to do with vbscript, but doing it with bash WITHOUT cheating and installing postfix, is kicking my fanny.
Can anyone help out please?

Here's my .mainrc:
---------
set verbose
set smtp=server.domain.com
set from=from@email.com
set smtp-auth=login
set smtp-auth-user=username
set smtp-auth-password=password
----------

---

