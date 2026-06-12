---
title: "SMB Password"
date: 2006-08-03
forum: Desktop Environments
---

### Post by nightmare03 on 2006-08-03
Hi, i hope this is the right place.

Im trying to password some of my SMB shares, i can access them fine without a password but when i limit the share to a user it will ask for the username and password but it won't accept them.

I've used smbpasswd in the terminal etc... 

I have this entry in /etc/samba/smb.conf

[80GBw]
path = /mnt/80
comment = 80GBw
available = yes
browseable = yes
valid users = network
public = yes
writable = yes

If i remove "valid users = network" i can access the share fine, if i leave it there it will ask me for a username and password but it wont accept the ones i assigned for that user.

Any help would be appreciated!

Thanks.

Damn its in the wrong place, i think i clicked the wrong link, sorry!

---

### Post by DarkNemesis618 on 2006-08-03
You may have already done this but here goes

```
smbpasswd -a username
smbpasswd username
```

then enter your password twice.

Also, restart the samba service.

I know that's all I had to do get mine working, although I didn't have that valid users line.

Hope that helps.

---

