---
title: "(Probably simple) Samba issue: ERRinvnetname..."
date: 2009-05-08
forum: General Help
---

### Post by karasune on 2009-05-08
Hi everyone...

I'm having a (probably trivial) issue with Samba. I'm trying to mount a Windows share from a NAS unit. Doing so when mounting different shares has never been a problem before, but after running 
```
sudo mount -t smbfs //[servername]/[sharename] /mnt/floppy -o username=[mydomain]\\scorbett
```I get the following error message:
```
tree connect failed: ERRSRV - ERRinvnetname (Invalid network name in tree connect.)
SMB connection failed.
```I'm not sure why I'm getting this error; smbclient shows that the share is available. Is there something wrong on the server side? Is it the client? I've never had this problem before, and after about an hour of looking I coudln't find anything that matched my problem.. any ideas?

Side note: I can't use CIFS mount because the box I'm mounting from is sufficiently old to not support it, and I can't upgrade the box (can't afford the downtime / messing up).

---

### Post by Alekz_ on 2009-05-08
Hi karasune!

You should consider the share name as case sensitive... It's a possibility!

One more thing! Are you using the server name or IP addr? If it's the server name, check you /etc/hosts file (assuming that you doesn't have a DNS server!)

Try it and tell us!

---

### Post by karasune on 2009-05-08
The share name case matches the case on the server, so I don't think that's it... I'll poke around with it though.

I've tried using both the IP and the hostname (DNS resolves the latter, thankfully); same error either way.

Thanks for the suggestions, Alexz_ :). Anything else I might try?

---

