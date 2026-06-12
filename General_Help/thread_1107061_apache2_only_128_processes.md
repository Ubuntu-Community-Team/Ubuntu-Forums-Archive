---
title: "apache2 only 128 processes"
date: 2009-03-26
forum: General Help
---

### Post by tscbh on 2009-03-26
I don't know where to post this topic. So please forgive me if it's in the wrong forums.

I am using:

[LIST]
[*]Ubuntu 8.10
[*]Apache 2
[/LIST]
I got the following partial configuration for apache server:
```
<IfModule mpm_prefork_module>
    StartServers         25
    MinSpareServers      25
    MaxSpareServers      50
    ServerLimit        1500
    MaxClients         1500
    MaxRequestsPerChild   0
</IfModule>
```

My server can only seemed to handle 128 http connections. Here is the output from pstree:
```

init-+-acpid
     |-apache2-+-128*[apache2]
     |         `-sh---php
     |-atd
     |-cron
     |-dd
     |-firewall.py
     |-6*[getty]
     |-klogd
     |-pure-authd
     |-pure-ftpd
     |-pure-uploadscri
     |-sshd-+-sshd---sshd---bash---pstree
     |      `-sshd---sshd---bash
     |-syslogd
     `-udevd
```

I got my own dynamic firewall scripts, but I tried to turn it off. But the problem is still there. I cannot surf the web on that server. I got another server with exactly the same hardware and configuration. It's running OK!

Would anybody shed some light?

Thanks in advance!

---

### Post by pennacook on 2009-03-26
your pstree output means 128 processes are started, not that 128 connections are allowed.

---

