---
title: "Trouble mounting windows share"
date: 2006-01-03
forum: Desktop Environments
---

### Post by thekidder on 2006-01-03
I'm trying to mount My Documents on a networked computer running Windows, but I get the error 
```
[mntent]: line 10 in /etc/fstab is bad

```
The line looks like this:```

//192.168.0.101/My Documents       /media/mydocs  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```
If I go into Places -> Network Servers, I can access it fine.

---

### Post by TrinitronX on 2006-01-03
The reason for this is that there is a space in the share name "My Documents".  Because the arguments in fstab are separated by whitespace, it thinks that 'Documents' is being given as the second argument (as a mount point).  Instead of a space in your fstab, use the escape sequence **\040** .

So the line would be: ```
//192.168.0.101/My**\040**Documents       /media/mydocs  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```

---

### Post by thekidder on 2006-01-03
Thanks :) . I thought it might be something like that, but I didn't know what to put there instead of a space.

---

### Post by el3ktro on 2006-02-11
Hi, 
I want to do the eact oposite, something like "mount /dev/sda3 /media/My Documents" in fstab, but I can't figure how to handle a whitespaced mount point in fstab. Your \40 escaping thing didn't work this way round. Any other ideas?

Tom

---

### Post by TrinitronX on 2006-02-12
Are you sure you're using "\040" and not just "\40"?
You could also try using "\0x20" if it takes hex escape sequences.

---

