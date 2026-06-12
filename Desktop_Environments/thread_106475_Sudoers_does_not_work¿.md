---
title: "Sudoers does not work¿?"
date: 2005-12-20
forum: Desktop Environments
---

### Post by DJ Ubuntu on 2005-12-20
I had re-to install Ubuntu to leave him more space physical, the subject is that I begin by the 5,04 and soon through aptitude dist-upgrade I pass me to the 5.10.  All this one work because of the modem and drivers USB of modem ADSL.

The only problem that I have is that I published the file sudoers of this one form:
Defaults !lecture,tty_tickets,!fqdn

```
# User privilege specification
root ALL=(ALL) ALL
jack ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

I like to let it thus not to have to use I sudo in each short while, the problem is that me she continues it requesting password.  MY question is if I have something in those lines badly??.
What think?  I do not want that it requests me plus pass when executing I sweat.
I do not want that I sweat requests but password to me.

Sorry for my bad english.:( 
Regards

---

### Post by mtron on 2005-12-21
well, if i got you right, you just want a root terminal. so open a terminal, type "sudo -s -H", enter your Password, and it won't bother you any more...

;) Cheers

---

