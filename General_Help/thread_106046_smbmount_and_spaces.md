---
title: "smbmount and spaces"
date: 2005-12-19
forum: General Help
---

### Post by thermopyl on 2005-12-19
Hi
I am trying to mount a smbshare in the fstab file but it the smbmount command doesn't like the space ->

//192.168.0.3/Backup/**My Music**	/media/MyMusic	smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0

I have tried underscore, \ and even %20! can anyone tell me how to do this?

Thanks

---

### Post by matw on 2005-12-19
This is just a guess, but you might try enclosing the entire address argument in quotes. like:

"//192.168.0.3/Backup/My Music"

---

### Post by healychan on 2005-12-19
[QUOTE=thermopyl]Hi
I am trying to mount a smbshare in the fstab file but it the smbmount command doesn't like the space ->

//192.168.0.3/Backup/**My Music**	/media/MyMusic	smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0

I have tried underscore, \ and even %20! can anyone tell me how to do this?

Thanks[/QUOTE]

Please try this:

//192.168.0.3/Backup/My\ Music/media/My\ Music smbfs

You better copy and paste rather than typing the whole thing

---

### Post by thermopyl on 2005-12-20
thanks guys but...

both methods give me:

10973: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

anyone have any other suggestions???

Thanks

---

### Post by matw on 2005-12-21
Have you tried getting a list of available shares using smbclient?

$ smbclient -L //192.168.0.3 -U <username>

That ought to at least help make sure you have the share name spelled correctly.

Hmm ... this is another guess, but I notice your share name is really long. It looks like Backup is the share name and My Music is a sub folder. If so, then try mounting just the share and then navigating to My Music once it's on your linux file system. Alternatively, make a new share on you windows box that is the My Music share.

HTH

---

### Post by senectus on 2006-02-09
If I do that I get this:
```
session setup failed: NT_STATUS_LOGON_FAILURE
```

---

