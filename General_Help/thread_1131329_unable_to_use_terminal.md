---
title: "unable to use terminal"
date: 2009-04-20
forum: General Help
---

### Post by jthillier on 2009-04-20
when ever i try to use my terminal to install a package or anything i get this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


any help would be apprciated

---

### Post by sisco311 on 2009-04-20
run:
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by jthillier on 2009-04-20
i tried that but i got the message
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0056' near line 1:
 newline in field name `#padding'
```

---

### Post by jthillier on 2009-04-20
bump

i have no idea whats wrong??

---

### Post by jimbren on 2009-04-20
If you tried 
```
sudo dpkg --configure -a
``` 
and you're still having problems, I would try
```
sudo apt-get -f install
```

The problem is that something you tried to install previously was left only paritially installed for whatever reason.  In my experience, this often has to do with some unresolved dependancy and the system tried to get through but couldn't for whatever resason.  

By running the first command, you're telling the system to reconfigure any unconfigured packages.  By running the apg-get command, you're telling the system to reconfigure/fix any packages that are either broken or not completely installed.  It is entirely possible that there's a problem with a dependant package, and not whatever you actually installed the last time you were able to install.

Make sense?

jim

---

### Post by jthillier on 2009-04-20
i still have the same problem 
> john@john-laptop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0056' near line 1:
 newline in field name `#padding'
john@john-laptop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


---

### Post by jthillier on 2009-04-20
Bump!!!

---

### Post by jthillier on 2009-04-20
bump

---

### Post by jimbren on 2009-04-21
1) Look through this thread and give it a shot.  

[http://www.linux-solved.com/post/SOLVED-DPKG-to-Segfault-26643.html](http://www.linux-solved.com/post/SOLVED-DPKG-to-Segfault-26643.html)

2) The whole 'bump' thing, for me at least, is incredibly irritating.  You're asking people for help.  Have a little patience and humility.

my .02


jimbo

---

