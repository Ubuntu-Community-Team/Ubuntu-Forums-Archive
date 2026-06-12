---
title: "MailScanner - folders disappear after reboot"
date: 2006-07-05
forum: Desktop Environments
---

### Post by northface on 2006-07-05
I have set up Postfix + Courier-imap + MailScanner + SpamAssassin + clamav on a Dapper Drake machine. It's seems to work well.

BUT - when I reboot my computer the folder /MailScanner/ in /var/run/MailScanner/ and the folder /subsys/ in /var/lock/subsys/ disappear. Has anyone experienced this and could give me a hint what to do?

Thank You.

---

### Post by ariek on 2006-07-20
I'm having the same problem here. I used to run MailScanner on my Hoary server without a problem. My system is AMD64.

---

### Post by northface on 2006-07-22
Thanks for your response. I have noticed a lot of MailScanner/Dapper users have this problem. But so far I have seen no solution.

I made a fresh installation on the server version of Dapper as well ... but no success.

---

### Post by northface on 2006-08-08
I did a workaround that seems to work - move the disappearing folders.

Change: /var/lock/subsys/MailScanner
To: /var/subsys/MailScanner

Change: /var/run/MailScanner
To: /var/MailScanner

sudo chown -R postfix:postfix /var/spool/MailScanner
sudo chown -R postfix:postfix /var/lib/MailScanner
sudo chown -R postfix:postfix /var/MailScanner
sudo chown -R postfix:postfix /var/subsys/MailScanner

Change to the new paths in:
/etc/rc2.d/S20mailscanner (6 locations)
/etc/MailScanner/MailScanner.conf (2 locations)

---

