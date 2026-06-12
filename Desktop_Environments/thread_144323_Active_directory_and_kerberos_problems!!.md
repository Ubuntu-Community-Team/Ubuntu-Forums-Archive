---
title: "Active directory and kerberos problems!!"
date: 2006-03-14
forum: Desktop Environments
---

### Post by scav on 2006-03-14
Hi, Ive joined my machine in an active directory network, everything works fine except one thing!

If i set on the server "change password on next logon", I aint prompted for a password change i just get access denied!

my common-auth look like this:

auth        required      pam_cups.so debug
auth        required      pam_mount.so use_first_pass
auth        sufficient     pam_env.so debug
auth        sufficient    pam_unix.so use_first_pass likeauth nullok
auth     sufficient    pam_krb5.so use_first_pass forwardable=true max_timeout=5 debug
#auth [default=done]    pam_ccreds.so action=validate use_first_pass debug
#auth [default=done] pam_ccreds.so action=store debug
#auth [default=done] pam_ccreds.so      action=update debug
auth        sufficient    pam_winbind.so use_first_pass
auth        required      pam_deny.so


and my login:

is the default shipped with breezy

here is the error message i get:

Mar 14 08:43:42 localhost login[12409]: pam_krb5: pam_sm_authenticate(login rvs_meg): entry:
Mar 14 08:43:42 localhost login[12409]: pam_krb5: pam_sm_authenticate(login rvs_meg): krb5_get_init_creds_password(): Password has expired
Mar 14 08:43:42 localhost login[12409]: pam_krb5: pam_sm_authenticate(login rvs_meg): exit: failure
Mar 14 08:43:42 localhost pam_winbind[12409]: request failed: Must change password, PAM error was 12, NT error was NT_STATUS_PASSWORD_MUST_CHANGEMar 14 08:43:42 localhost pam_winbind[12409]: user `rvs_meg' new password required
Mar 14 08:43:45 localhost login[12409]: FAILED LOGIN (1) on `tty4' FOR `rvs_meg', Authentication token is no longer valid; new one required.

---

### Post by fmo on 2006-03-14
I kind of remember that there is some problems with Samba and AD in the version of Samba in the repository (3.0.14a) that have been fixed in the last release (3.0.21c), I'm not sure that your problem is related but I might be worth having a look at [www.samba.org](www.samba.org)

---

### Post by nocturn on 2006-03-14
pam_krb5 doesn't seem to support required password changes.  I have the same issue in an OpenLDAP/MIT Kerberos environment.

---

### Post by scav on 2006-03-14
[QUOTE=nocturn]pam_krb5 doesn't seem to support required password changes.  I have the same issue in an OpenLDAP/MIT Kerberos environment.[/QUOTE]
It doest, I have it working on a Fedora Core machine

---

### Post by scav on 2006-03-14
it worked after updating samba to a new version and leave and join the domain!

strange though

---

