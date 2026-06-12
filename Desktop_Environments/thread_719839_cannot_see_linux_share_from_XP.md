---
title: "cannot see linux share from XP"
date: 2008-03-09
forum: Desktop Environments
---

### Post by keratos on 2008-03-09
So, i setup "Shared Folder" from ubuntu system menu and shared this as "Windows Network (SMB)"

From my XP machine I can see my linux box. If i try to click it in networks, I get a logon screen ??? If I try and map a network drive, I can see the linux box but no shares?

Help?

---

### Post by soldats on 2008-03-09
I believe you need to set up a samba network sort of passphrase. I think its stated in the samba section of the help pages. I havent used it in a long while. If i get some extra time I'll look it up if you dont find it.

---

### Post by keratos on 2008-03-09
> **soldats said:**
> I believe you need to set up a samba network sort of passphrase. I think its stated in the samba section of the help pages. I havent used it in a long while. If i get some extra time I'll look it up if you dont find it.

What does that mean and entail? 

I'm relatively new to linux but pretty conversant with XP.

Is the issue in linux or XP?

---

### Post by keratos on 2008-03-09
in /etc/samba/smb.conf

change 
```

security = user

```

to
```

security = share

```

Works now!

---

