---
title: "Fetchmail and Maildrop"
date: 2006-07-12
forum: Desktop Environments
---

### Post by ChrisDerson on 2006-07-12
I setup fetchmail using 'fetchmailconf' to deliver via the maildrop mda.  Tested as my normal user and it seemed to work Ok.
To automate I tried:
[LIST]
[*]Move ~/.fetchmailrc to /etc/fetchmailrc
[*]Change /etc/default/fetchmail so START_DAEMON=yes
[*]Did /etc/init.d/fetchmail start
[/LIST]
Nothing happened - test mail sent from external account never turned up.
Checked syslog, and found Maildrop was returning error 75.
Ran fetchmail in debug mode (/etc/init.d/fetchmail debug-run) and discovered that "/usr/bin/maildrop: Cannot set my user or group id.".
After much tinkering I got it working by:
[LIST]
[*]Edit /etc/init.d/fetchmail so $USER=mail not fetchmail
[*]Changed owner of /var/lib/fetchmail from fetchmail to mail
[*]Ensured SUID bin on /usr/bin/maildrop set
[/LIST]
Now it all works.
If anybody needs more detail on setting up this configuration, I'll be happy to write a step-by-step guide.

I hope somebody else finds this information useful, but I have a question:
Is this the best way to setup fetchmail and maildrop?  I know I could have re-compiled fetchmail to add fetchmail as a trusted user, but then I would have problems on the next upgrade of maildrop.

---

