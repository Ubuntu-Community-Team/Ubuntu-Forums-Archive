---
title: "Problem in /etc/profile"
date: 2009-01-22
forum: General Help
---

### Post by Zeratul021 on 2009-01-22
Hi all, earlier today i was attempting to upgrade my server with aptitude upgrade but it failed with reason: cannot find path to ldconfig, rc-update ... 4 total. I went to /etc/profile and assumed that im in wrong branch of condition determining PATH, so I edited it to look the same.
What i quite dont understand is the condition:

```
if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else                                                                              
  PATH="/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games:/sbin:/usr/sbin:/usr/local/sbin"
fi
```

As you can see the second path has "sbins" added. My question is why i was turned into the else branch of the statement therefor what does the condition mean?
Thanks, with regards,
Marek

---

### Post by Titan8990 on 2009-01-22
The condition is this:


if the result of the command id -u = 0 then the first path is used. id -u will only = 0 if ran by the root user. So basically that line says:

IF root use first path

else, use this alternate path



You should change your paths in ~/.bash_profile instead of /etc/profile

---

### Post by Zeratul021 on 2009-01-22
Thanks, thing is i find it strange that when upgrading packages what requiers one to be root system sets the path that doesn't contain paths to programs needed by upgrade.
Anyway, thanks for clarification :)

---

