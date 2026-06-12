---
title: "Flurdy's Postfix guide"
date: 2006-03-21
forum: Desktop Environments
---

### Post by Blairboy on 2006-03-21
For the most part, everything's going well.  I just ran into a small problem with a few things:

In the Authentication section, there is the part where you edit /etc/courier/imapd and then the guide says "If you need Pop, modify the pop file as well."  The only problem is that the options for imap (IMAP_CAPABILITY="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE") don't exist in the pop3d file.  

But the bigger issue I'm having is with courier.  when i run courier-authdaemon I get this:

 * Starting Courier authdaemon... /etc/courier/authdaemonrc: line 70: MYSQL_SERVER: command not found
/etc/courier/authdaemonrc: line 71: MYSQL_USERNAME: command not found
/etc/courier/authdaemonrc: line 72: MYSQL_PASSWORD: command not found
/etc/courier/authdaemonrc: line 73: MYSQL_PORT: command not found
/etc/courier/authdaemonrc: line 74: MYSQL_OPT: command not found
/etc/courier/authdaemonrc: line 75: MYSQL_DATABASE: command not found
/etc/courier/authdaemonrc: line 76: MYSQL_USER_TABLE: command not found
/etc/courier/authdaemonrc: line 80: MYSQL_CLEAR_PWFIELD: command not found
/etc/courier/authdaemonrc: line 81: MYSQL_UID_FIELD: command not found
/etc/courier/authdaemonrc: line 82: MYSQL_GID_FIELD: command not found
/etc/courier/authdaemonrc: line 83: MYSQL_LOGIN_FIELD: command not found
/etc/courier/authdaemonrc: line 84: MYSQL_HOME_FIELD: command not found
/etc/courier/authdaemonrc: line 85: MYSQL_NAME_FIELD: command not found
/etc/courier/authdaemonrc: line 86: syntax error near unexpected token `('
/etc/courier/authdaemonrc: line 86: `MYSQL_MAILDIR_FIELD concat(home,'/',maildir)'

Also, I set up squirrelmail according to the howto, but when I go to webmail.mydomain.com, nothing loads.  I checked the squirrelmail log and all it said was "File does not exist: /var/www/squirrelmail/favicon.ico"

This is yet another error I get "Mar 21 04:15:27 localhost postfix/master[7302]: fatal: /etc/postfix/master.cf: line 24: bad transport type: mime_header_checks="

I'm so close to done, can anyone help me with this?

---

