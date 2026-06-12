---
title: "Problem installing packages"
date: 2009-04-24
forum: General Help
---

### Post by mc6415 on 2009-04-24
Right I'll keep this short and sweet, recently whenever I go to install any package I end up getting the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32nss-mdns ttf-liberation winbind wine-gecko
Suggested packages:
  msttcorefonts
The following NEW packages will be installed
  lib32nss-mdns ttf-liberation winbind wine wine-gecko
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/18.2MB of archives.
After this operation, 74.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `igest,' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)


And it fails to install, can anyone help me here?

Thanks,
Coombes

---

### Post by Kareeser on 2009-04-24
Weird. Have you modified the file /var/lib/dpkg/available in any way?

---

### Post by mc6415 on 2009-04-24
Well I took a look at that file and from the error message it would seem the problem lies in this little block:

igest, NTLM, and Basic authentication
  * Server support for Digest and Basic authentication
  * Basic client-side SOAP and XML-RPC support

Now I was thinking if possible would you be able to compare this to the start of your var/lib/dpkg/available or anyone else that is and see where it doesn't match up as that could possibly be a quick fix. Thanks for the speedy response.

---

### Post by mc6415 on 2009-04-24
All is good managed to solve the problem by doing:

dpkg --clear-avail
apt-get update

---

