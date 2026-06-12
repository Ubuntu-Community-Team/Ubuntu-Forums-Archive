---
title: "I get this error when it tells me to run update manager ."
date: 2007-06-28
forum: Dell  Ubuntu Support
---

### Post by ross350 on 2007-06-28
Hi
things have been a bit shaky for me over the last couple of days after learning of ubuntu.
Learning to love it that is. but yeh this isn't a fan post.

Fellow users I have a problem. 
when i first login I get the orange square in the top corner(might be different for some people but i haven't changed it around too much) anyway, the square tells me i need to run package manager ,
so, i do 
and it gives me this error:-

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

can i just reinstall the package manager or what do i do, the system runs fin and i have beryl finaly working after figuring out what login as xgl meant.

an i have some help
Ross

---

### Post by bapoumba on 2007-06-28
Hello!
Could you please open a terminal (> Applications > Terminal), run :
```
sudo aptitude update
```
and paste the complete output.

Paste also your sources.list:
```
cat /etc/apt/sources.list
```

---

