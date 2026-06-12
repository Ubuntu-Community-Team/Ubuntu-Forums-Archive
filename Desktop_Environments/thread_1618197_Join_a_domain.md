---
title: "Join a domain"
date: 2010-11-10
forum: Desktop Environments
---

### Post by 1opstrader1 on 2010-11-10
Hi Group,

I am using Ubuntu 10.10 and trying to login to a Windows server 2008 R2 domain controller.
I am using likewise Open 5.4 to accomplish this. Everytime I run the command to join the domain,

sudo domainjoin-cli join sbserver administrator

I receive the following error:

could not acquire Kerberos ticket
+WARNING
Kerberos requires administrator's password
to have been reset once since domain install
in order to add DES encryption keys to user
account which only has a RC4 key when
initially created.
[ERROR]
returned error code 6

OR

9502 (0x251E) DNS_ERROR_BAD_PACKET - A bad packet was received from a DNS server. Potentially
the requested address does not exist.

I am able to ping the DNS server via name and ip address and from the server/network I am able to ping back to the client, so I am confused as how this is a DNS issue.

Any help would be much appreciated.

Thanks - Ron

---

### Post by SlugSlug on 2010-11-10
try 
```
net join -W [COLOR=Red]domainname [/COLOR]-S [COLOR=Red]domaincontroller.domain.lan[/COLOR] -U administrator
```

or

```
net join -W [COLOR=Red]domainname [/COLOR]-S [COLOR=Red]domaincontroller.domain.lan[/COLOR] -U Administrator
```

---

### Post by 1opstrader1 on 2010-11-10
Hi slug,

Thanks for the reply. I tried what you suggested and here is the output:

rbrown@ubuntulaptop:~$ net join -W sbserver -S dc1.sbserver.local -U administrator
[2010/11/10 11:20:07.026752,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2010/11/10 11:20:07.026947,  0] utils/net_rpc.c:368(rpc_oldjoin_internals)
  error storing domain sid for SBSERVER.LOCAL
Enter administrator's password:
[2010/11/10 11:20:13.275147,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2010/11/10 11:20:13.275240,  0] utils/net_rpc_join.c:457(net_rpc_join_newstyle)
  error storing domain sid for SBSERVER
Unable to join domain SBSERVER.

I did try both way and the output was the same.

Thanks

---

### Post by SlugSlug on 2010-11-10
Hi yer sorry about that just tried it again here.. looks like thats what I first did.. but didn't peruse as was no real need.. we access the linux box via samba.

---

### Post by 1opstrader1 on 2010-11-10
I was about to try try samba now myself. 

After doing some reading, samba needs krb and openldap. Is there anything else?

What do you think about using webmin to accomplish this?

---

### Post by SlugSlug on 2010-11-10
I wouldn't bother with webmin for samba, (useful for other things)

samba is failry straight forward, on one box I have it open to all, on the other it's controlled via Windows Active Directory..  which gets a little more complex

---

