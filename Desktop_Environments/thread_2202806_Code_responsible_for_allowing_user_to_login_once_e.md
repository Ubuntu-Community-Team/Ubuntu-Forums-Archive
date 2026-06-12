---
title: "Code responsible for allowing user to login once entering the correct password"
date: 2014-01-31
forum: Desktop Environments
---

### Post by lee_can on 2014-01-31
How can i find the responsible code which allow user to enter his password and to verify if the password is correct during login in process.

Best Regards

---

### Post by Lars Noodén on 2014-01-31
That would probably be in the package [login](http://packages.ubuntu.com/saucy/login).  You can check out the source package (deb-src) and look there.

---

### Post by SeijiSensei on 2014-01-31
Linux uses "pluggable authentication modules" to handle user authentication.  Modules provide access to various backends like the password file or an LDAP server.  The directory /etc/pam.d contains the configuration files for various applications.  The file /etc/pam.d/login contains the directives that handle ordinary logins.  It invokes the "common-*" files that supply the code to use the password file.

If you are looking for source code, you might want to start here: [https://fedorahosted.org/linux-pam/](https://fedorahosted.org/linux-pam/)

However if you're simply interested in the method for obtaining and verifying user credentials, then the login package Lars mentioned may be all you need.

---

