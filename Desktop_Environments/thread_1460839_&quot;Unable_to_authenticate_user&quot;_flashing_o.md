---
title: "&quot;Unable to authenticate user&quot; flashing on startup"
date: 2010-04-23
forum: Desktop Environments
---

### Post by zak_neutron on 2010-04-23
Help

My login screen (gdm)is stuck in a perpetual flashing loop of saying "unable to authenticate user". No keystrokes appear to get me out of the loop.

The only access I can get is via ssh. So I have full access to all log files.

Using htop the only GDM processes that appears to running are:

```
/usr/lib/gdm/gdm-simple-greeter
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-nxADJS/database -nolisten tcp vt7
```

output of uname -a:

```
Linux :):):):):) 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

I think the error occured when I ran the default script of "adduser" with a username of "person1 & person2" - I think the script resented the ampersand character. The script appeared to hang - I have tried to delete the user account (I think it created "person1" user account) - but this does not fix the login problem.

Please let me know what log files I need to present back to help diagnose the problem. "dmesg" and /var/log/messages does not appear to have anything related to gdm or login cited.

Thanks

---

### Post by zak_neutron on 2010-04-24
Bump!

---

### Post by zak_neutron on 2010-04-24
:redface: sorted it - ssh into the machine and deleted the offending account - in the /etc/passwd file there was some weird characters on the same line as this offending account - this must have caused either gdm or pm a problem!!!

Lesson learned!

SOLVED!

---

