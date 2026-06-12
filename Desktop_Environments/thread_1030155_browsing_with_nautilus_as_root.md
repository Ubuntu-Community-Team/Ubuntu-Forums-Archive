---
title: "browsing with nautilus as root"
date: 2009-01-04
forum: Desktop Environments
---

### Post by cybernet on 2009-01-04
```
(nautilus:6439): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6439): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///var/lib/mysql
--> file:///media/disk/bk/mysql

(nautilus:6439): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:6439): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown

```

what this error means

```
--- Hash table keys for warning below:
--> file:///var/lib/mysql
--> file:///media/disk/bk/mysql
```

---

### Post by fazza on 2009-04-09
um sorry I can't really help, but I have a possibly related issue to tag on the end... When I'm using a root nautilus browser, no protocols work whatsoever. Things like /home/user/Desktop shows me that Desktop folder, but if I go to anything like computer:/// or network:/// , it throws up an error saying nautilus does not know how to handle those protocols. Well, I know it does, cos I use them all the time... so I wondered, is this a bug or a system-protection lockdown sort of thing?

Thanks

and sorry I couldn't help you cybernet :S

---

### Post by fazza on 2009-04-09
bump

---

### Post by nathanpc on 2009-04-09
I am not sure but i think this error means that when you run Nautilus as root it cant  mount this path that is for mysql.

Nathan Paulino Campos

---

### Post by askreet on 2009-04-09
Why are you all using Nautilis as root?  That just sounds like a terrible idea.

---

### Post by fazza on 2009-04-09
why? I use it to move files around regularly

---

### Post by niteshifter on 2009-04-10
> **fazza said:**
> why? I use it to move files around regularly

Give it time. Someday you'll join the Used To Root Nautilus Club, and you'll have your very own horror story as to how you got there ;)

---

