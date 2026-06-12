---
title: "Secondary groups do not show up in corporate domain setup."
date: 2009-03-17
forum: General Help
---

### Post by Jwav3 on 2009-03-17
Hi, I work in a small office where we use Ubuntu Hardy internally on the desktop. It's not a complicated setup, we use a NFS exported /home and OpenLDAP for authentication.

We have this nagging little problem nobody here has been able to figure out, one of our users constantly complains about write problems to a NFS share. On investigating this problem it because apparent that this users secondary groups were not appearing.

```
$ id
uid=15001(user) gid=15001(user) groups=15001(user)
```

Instead of what is expected (and what every other user has)
```
$ id
uid=15001(user) gid=15001(user) groups=24(cdrom),44(video),46(plugdev),15001(user),20001(hr)
```

The unusual thing is that is only for gnome.. if you su - or ssh into the system, the groups show up normally. The problem only seems to be with gnome.

What we have tried so far:
1. Recreated account in ldap server.
2. Attempted logon on diffrent client systems.
3. Reimaged workstation.
4. Recreated users gnome profile.
5. Authenticated against an entirely septate ldap server.

On the last one 5. this worked for a few weeks.. ?? Not sure why, now both ldap servers produce the same results. They are not connected to each other.

We are out of ideas.. where should we look? Only one user out of 15 have this problem and the setup's are identical. How does gnome's logon fall to grab these groups but everything else picks them up just fine. What does it do differently?

---

### Post by Jwav3 on 2009-03-18
Wanted to add.. if we do

ssh -X localhost 

Then launch the programs (like nautilus) they pick up the secondary groups just fine for this user. Weird.

---

### Post by Jwav3 on 2009-04-13
bump, problem still exists.

---

