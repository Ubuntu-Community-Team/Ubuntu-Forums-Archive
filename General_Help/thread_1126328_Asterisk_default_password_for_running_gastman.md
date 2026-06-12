---
title: "Asterisk default password for running gastman?"
date: 2009-04-15
forum: General Help
---

### Post by pinkunicorn on 2009-04-15
I just installed Jaunty to use as an Asterisk machine, and installed gastman to configure it.

When I run gastman, it brings up a dialog asking for the host name. I enter the IP address of the machine since I want to configure the local Asterisk on this machine. After that, I get a dialog asking for username and password. Asterisk was installed with apt-get; I have no idea what the password might be.

I have tried admin/admin, the user/password I use to log in on the machine itself and no password to no avail.

What should I do to connect to my local Asterisk installation?

---

### Post by Elludium_Q-36 on 2009-04-30
Asterisk will not jump and dance 'till you teach it to do so...

You must create that username & password.

/etc/asterisk/manager.conf
/etc/asterisk/users.conf
/etc/asterisk/dundi.conf

Do you have a sudo kate?

Forget not about destar & op-panel 

...

..

.

---

