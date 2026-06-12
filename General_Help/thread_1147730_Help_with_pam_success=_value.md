---
title: "Help with pam success= value"
date: 2009-05-03
forum: General Help
---

### Post by bagpussnz on 2009-05-03
Hi,
I have a number of ubuntu 8.10 users. Seemingly at random these users cannot login.
When this happens, we see the pam files common-auth, common-password and common-account have changed.
We believe this is due to an update - but haven't pinned it down to a particular one.

We see the success= values are changed to 1, i.e.,

auth	[success=1 default=ignore]	pam_unix.so nullok_secure

In order to make it work again, we have found we need to change the success= values to 2 in common-auth and common-password and to 3 in common-account.

However, I don't know why. Can anyone explain what these values mean?

Regards,
Ian.

---

### Post by Jope on 2011-03-25
You probably already found this out for yourself, but moments ago I had the same problem, was googling around for the solution and found this thread.

In the end I read the manual for pam.d more carefully, and this is what it told me:

> 
For the more complicated syntax valid control values have the following form:

[value1=action1 value2=action2 ...]

Where valueN corresponds to the return code from the function invoked in the module for which the line is defined.

It is selected from one of these: success, open_err, symbol_err, service_err, system_err, buf_err, perm_denied, auth_err, cred_insufficient, authinfo_unavail, user_unknown, maxtries, new_authtok_reqd, acct_expired, session_err, cred_unavail, cred_expired, cred_err, no_module_data, conv_err, authtok_err, authtok_recover_err, authtok_lock_busy, authtok_disable_aging, try_again, ignore, abort, authtok_expired, module_unknown, bad_item, conv_again, incomplete, and default.

       The last of these, default, implies ´all valueN´s not mentioned explicitly. Note, the full list of PAM errors is available in /usr/include/security/_pam_types.h.

**The actionN can be: an unsigned integer, n, signifying an action of ´jump over the next n modules in the stack´; or take one of the following forms:**


So it's just how many modules to skip if this is successful. Usually the default pam config segments contain a pam_deny.so right after the auth modules. The number must be set just high enough to skip the rest of the auth modules including pam_deny.so

---

