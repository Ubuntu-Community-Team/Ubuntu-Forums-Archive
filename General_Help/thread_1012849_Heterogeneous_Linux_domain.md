---
title: "Heterogeneous Linux domain"
date: 2008-12-16
forum: General Help
---

### Post by jbhedgehog on 2008-12-16
I'm started my basic research on setting up a fully Linux domain (a la MSFT's Active Directory).  I have some of the basics down, such as file shares and print servers.

However, I'm not finding any sort of documentation or information regarding how to create a complete Linux domain.  You know, where there is a central server with a single logon, some sort of group permissions.

I'm quite used to AD, so I'd really like to stick with something like that.  A GUI would be dandy...although that might be frowned upon in the Linux world.

I'm a recovering MSFT MCSE, so I still live in the MSFT world a lot.

Any information would be really appreciated.

Thanks,
JBH

---

### Post by nielz on 2008-12-16
Well, active directory is basically glorified ldap+kerberos, so that's what you're looking to setup. Instead of cifs/smb nfs is often used on *nix networks for filesharing. The whole thing can be hard to setup though but it is most certainly possible to get it working properly, you do have to put some work into it though.

(You'll probably have to setup dns too, I've found dnsmasq to be very suitable for small networks)

(And sorry, no good gui that I know of, we *nix people write scripts for common taks :))

---

### Post by jbhedgehog on 2008-12-16
Hmmm...I'm wondering about the time invested in the project.

How about 1 AD server (under 100 users) with all Linux clients?  Are there gotchas there too?

I really want to keep costs low, that's why I'm on the Linux binge.

THX,
JBH

---

