---
title: "firefox and kerberos authentication"
date: 2006-06-16
forum: Desktop Environments
---

### Post by shrift on 2006-06-16
I am tryint to authenticate via kerberos to a local webserver we have here. Currently I have the following packages installed: krb5-clients krb5-config krb5-user and libkrb53. I am able to do a kinit and klist fine. That shows I have a ticket. However when I try to open the website I get this error:
```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Debian) mod_auth_kerb/5.0-rc6 PHP/4.4.2-1+b1 mod_ssl/2.0.55 OpenSSL/0.9.8b Server at hoffa.local.cityofevanston.org Port 80
```

and on the webserver error log I get this:
```
[Fri Jun 16 10:34:50 2006] [error] [client 10.1.20.225] request failed: error reading the headers
```

Any ideas?

---

