---
title: "How to prevent nepomuk starting a POP3 downloader?"
date: 2012-05-23
forum: Desktop Environments
---

### Post by jtappin on 2012-05-23
After installing Kubuntu 12.04 on my workstation (replacing Debian Squeeze), I initially tried using kmail to get my email via POP3, before giving up on it, and:
[LIST=1]
[*] switching to claws and
[*] mounting /var/mail from the mail server via NFS.
[/LIST]
Unfortunately every time I log in afresh, after a few minutes I get a password prompt for the POP 3 downloader. On checking with the system monitor I find that there is a nepomuk-pop3... process running [sorry I didn't note down the full name before killing it].

I can't find any option to prevent it starting it in "System settings", and the only mentions of pop3 that I can see in ~/.kde/share/... are pop3=false and pop3s=false on config/kdeglobals.

How do I prevent the pop3 scanner/downloader from starting?

---

