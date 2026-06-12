---
title: "OS X Server LDAP Authentication Problems"
date: 2009-01-05
forum: General Help
---

### Post by sliggy on 2009-01-05
Hey everyone,

I just followed [this](https://help.ubuntu.com/community/OSXLDAPClientAuthentication) guide on how to setup Ubuntu to authenticate with an Mac OS X 10.4 server. I followed the guide 100% and was left with the ability to see users by running 
```
getent passwd
and
getent passwd (user)
```
Which would come up with all the right information about the user. My problem is that I want those users to be able to login through the login prompt, which isn't working. When I login as my local user though, I get the usual username and password prompt, but then I get an LDAP password prompt, where I can type in anything and still login successfully. 

Any ideas on how to solve this? Thanks in advance!

---

### Post by decoherence on 2009-01-05
Try running ```
tail -f /var/log/auth.log
``` in another terminal during the login attempt and see if there are any clues.

Also, please confirm that you aren't able to login with GDM (the graphical login window) or any of the methods suggested in the document (su, ssh) or another login shell. If you've only tried with GDM, try one of the other methods and see if you log in or get some useful information.

thanks

---

### Post by sliggy on 2009-01-06
Thanks, now I can work with an actual error instead of guessing. 

The error I'm getting right now is 

```

nss_ldap: failed to bind to LDAP server [ip of server]: invalid credentials

```
and
```

nss_ldap: could not search LDAP server - Server is unavailable

```

---

### Post by sliggy on 2009-01-20
Sorry for the bump but has anyone found a solution to this?

---

