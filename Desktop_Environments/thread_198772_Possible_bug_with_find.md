---
title: "Possible bug with find?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by TheEvilHammer on 2006-06-17
I tried running a simple find command today on 6.06 and this is what happened:

[FONT="Courier New"]/etc/samba$ find / -name *smb*
find: paths must precede expression
usage: find [-H] [-L] [-P] [path...] [expression][/FONT]

I've used find a good deal, and I know for sure that my syntax is correct.  Plus, I can run that exact command on other Linux machines I have access to (one Fedora and one CentOS) without any problems.  Why would that command fail on Ubuntu?

---

### Post by Lord Illidan on 2006-06-17
Works here alright :

```
jean@ubuntu:/etc$ find / -name *smb*
find: /etc/lvm/backup: Permission denied
find: /etc/lvm/archive: Permission denied
find: /etc/ssl/private: Permission denied
find: /etc/cups/ssl: Permission denied

```

---

### Post by jpkotta on 2006-06-17
Use quotes to prevent shell expansion.```
find / -name '*smb*'
```

---

### Post by TheEvilHammer on 2006-06-17
Ah, that was it.  I had a couple files in that directory that matched *smb*, so the shell must have been really trying to run:

[FONT="Courier New"]find / -name smb.conf smb.conf.backup[/FONT]

That makes sense - thanks guys!

---

