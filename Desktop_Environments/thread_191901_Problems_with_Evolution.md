---
title: "Problems with Evolution"
date: 2006-06-08
forum: Desktop Environments
---

### Post by niels on 2006-06-08
I have just made a fresh install of Ubuntu 6.06 TLS. I have set up an email account with Evolution, but when I tries to read a mail Evolution just shots down. Now it shots down before I can do anything, because it tries to read the mails at startup. I have started Evolution in a terminal, and gets the folllowing error:
> niels@niels-laptop:~$ evolution --component=mail
CalDAV Eplugin starting up ...

(evolution-2.6:6427): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:6427): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:6427): camel-WARNING **: camel_exception_get_id called with NULL parameter.
niels@niels-laptop:~$


Doe's anyone knows how to address this problem.

---

### Post by Rondonjin on 2006-06-08
[QUOTE=niels]I have just made a fresh install of Ubuntu 6.06 TLS. I have set up an email account with Evolution, but when I tries to read a mail Evolution just shots down. Now it shots down before I can do anything, because it tries to read the mails at startup. I have started Evolution in a terminal, and gets the folllowing error:


Doe's anyone knows how to address this problem.[/QUOTE]

I get the same errors but it starts up OK. Try renaming your .evolution folder to .evolution.bak or something.

Wayne

---

