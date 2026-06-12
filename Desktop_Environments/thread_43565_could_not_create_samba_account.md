---
title: "could not create samba account"
date: 2005-06-22
forum: Desktop Environments
---

### Post by kapsiaoloong on 2005-06-22
root@loongx2:/home/baboon2 # sudo smbpasswd -a baboon
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
pdb_getsampwnam: Unable to open TDB passwd (/var/lib/samba/passdb.tdb)!
Failed to initialise SAM_ACCOUNT for user baboon. Does this user exist in the UNIX password database ?
Failed to modify password entry for user baboon

can anyone answer to my plea to the problem which i have posted ... i don seem to be able to create the samba account .. maybe i missed some thing along the way in setting up my samba any solutions is gratefully welcomed

---

### Post by fdoving on 2005-06-22
[QUOTE=kapsiaoloong]root@loongx2:/home/baboon2 # sudo smbpasswd -a baboon
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
pdb_getsampwnam: Unable to open TDB passwd (/var/lib/samba/passdb.tdb)!
Failed to initialise SAM_ACCOUNT for user baboon. Does this user exist in the UNIX password database ?
Failed to modify password entry for user baboon

can anyone answer to my plea to the problem which i have posted ... i don seem to be able to create the samba account .. maybe i missed some thing along the way in setting up my samba any solutions is gratefully welcomed[/QUOTE]
 does the user 'baboon' exist as a real user on the system? if not try to make one or modify smb.conf to not require it.

- Frode

---

