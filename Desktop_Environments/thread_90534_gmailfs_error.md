---
title: "gmailfs error"
date: 2005-11-15
forum: Desktop Environments
---

### Post by wammy on 2005-11-15
just installed the gmailfs package with synaptic and editted /etc/gmailfs/gmailfs.conf but i get errors when trying to connect:

###############
gmailfs.py:Gmailfs:unnamed mount options: ['']
gmailfs.py:Gmailfs:named mount options: {}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in log in
    raise GmailLoginFailure
libgmail.GmailLoginFailure
###############

logfile says:
###############
11/15/05 12:41:22 WARNING    OpenSSLProxy is missing. HTTPS proxy support disabled.
11/15/05 12:41:22 WARNING    mount: warning, should mount with username=gmailuser option, using default
11/15/05 12:41:22 WARNING    mount: warning, should mount with password=gmailpass option, using default
11/15/05 12:41:22 WARNING    mount: warning, should mount with fsname=name option, using default
###############


any ideas?

---

### Post by mgor on 2005-11-15
haven't used gmailfs myself, but it seems like there's something wrong with the username/password by looking at the logfile .. check your configuration file for any typos, syntax errors etc.

---

