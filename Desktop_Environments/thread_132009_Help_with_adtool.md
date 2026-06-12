---
title: "Help with adtool"
date: 2006-02-17
forum: Desktop Environments
---

### Post by dpack on 2006-02-17
I am running Breezy and installed adtool from the Synaptec Package Manager. I have configured the adtool.cfg file and can successfully connect to the uri ldap address. The problem is I keep getting Invalid Credentials every time I try to reset a password.

The error message:
```
bind: : Invalid credentials (49)
        additional info: 80090308: LdapErr: DSID-0C090334, comment: AcceptSecurityContext error, data 525, vece
error: Error in ldap_bind Invalid credentials
```

Content on the adtool.cfg file
```
## use ldaps:// for secure connection - needed for setpass to work
 uri ldap://msaexch01.my-domain.com
 binddn cn=Tech User,ou=Resources,dc=my-domain,dc=com
 bindpw secret
 searchbase ou=msa,dc=my-domain,dc=com
```

Of course I have substituted our real domain name for “my-domain” and “secret” is not the actual Tech User password.

The Tech User account I am using resides in the following tree path if you were looking in AD:
my-domain.com > MSA > Resources > Tech User

The actual username of Tech User is tuser but that is not what is supposed to go in the CN. I am at a loss on why I keep getting Invalid credentials. I have tried other user accounts in other containers but those don't work either.

Any ideas?

---

