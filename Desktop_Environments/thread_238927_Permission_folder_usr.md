---
title: "Permission folder /usr"
date: 2006-08-18
forum: Desktop Environments
---

### Post by mirr0r on 2006-08-18
Hi,

On my laptop I changed permission of /usr folder with command:
```
chmod -R 777 /usr 
```

From that time I had a lot of error in my ubuntu dapper 64 bit..
So I try this solution: 
1) checked an other clean installation on my desktop:right click on the /usr folder-> "property menu"  tell me numeric permission 1200755 
2) on my laptop command by root ```
chmod -R 755 /usr 
```

but numeric permission is 1600755 and problem persist...

How can I change 1600 to 1200 and what kind of permission are??  
Thanks and sorry for my bad english

---

### Post by infinito on 2006-08-18
I don't know an easy way to restore the permissions on /usr, but just wanted to say this:

PLEASE!! DON'T DO CHANGE PERMISSIONS ON /USR ALTOUGHT YOU KNOW WHAT YOU'RE DOING!

It's clear that you didn't know what you were doing...

---

