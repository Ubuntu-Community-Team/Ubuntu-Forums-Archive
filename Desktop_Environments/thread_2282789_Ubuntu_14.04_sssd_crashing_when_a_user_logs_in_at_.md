---
title: "Ubuntu 14.04 sssd crashing when a user logs in at the desktop"
date: 2015-06-16
forum: Desktop Environments
---

### Post by clintd2 on 2015-06-16
Hi,  

We are just starting to roll out Ubuntu 14.04 Desktops and are coming across a strange issue.  We are using sssd talking to a 389 LDAP server.  This generally works but when a user logs in at the desktop they often see an error dialog saying "System program problem detected" from looking in /var/crash it is clear that as some point sssd is crashing specifically /usr/lib/x86_64-linux-gnu/sssd/sssd_be.  Looking at the sssd logs we see

# cat /var/log/sssd/sssd_LDAP.log 
(Wed Jun 17 13:06:17 2015) [sssd[be[LDAP]]] [talloc_log_fn] (0x0010): talloc: access after free error - first free may be at ../src/providers/ldap/sdap_async_nested_groups.c:743
(Wed Jun 17 13:06:17 2015) [sssd[be[LDAP]]] [talloc_log_fn] (0x0010): Bad talloc magic value - access after free


sssd seems to continue working correctly after the crash

Web searching only seems to find old Fedora related posts that indicate this may have been a problem with sssd code in the past and nothing that is specific to ubuntu.
So first question, is there a better place to be asking about sssd issues? Secondly does anyone know of a fix for this?

Should I be logging a bug report at [https://bugs.launchpad.net/ubuntu/+source/sssd](https://bugs.launchpad.net/ubuntu/+source/sssd) ?

Thanks for any help you can offer.

More info about our setup is 

sssd Version: 1.11.5-1ubuntu3
Depends: sssd-common (= 1.11.5-1ubuntu3), sssd-ad (= 1.11.5-1ubuntu3), sssd-ipa (= 1.11.5-1ubuntu3), sssd-krb5 (= 1.11.5-1ubuntu3), sssd-ldap (= 1.11.5-1ubuntu3), sssd-proxy (= 1.11.5-1ubuntu3), python-sss (= 1.11.5-1ubuntu3)

---

