---
title: "Permissions issue"
date: 2009-04-20
forum: General Help
---

### Post by Rujiel on 2009-04-20
Any idea how a file could have no permissions under ls -l, but still be completely readable? I'm using a program called Fuse to simulate a file system, and it mounts a folder and creates a file in it with certain specifications.. such as no permissions.. but the file's still readable. Any idea why?

---

### Post by Rujiel on 2009-04-20
Sorry, I should have posted what I mean--

:~/Desktop/new2$ ls -l
total 0
---------- 1 root root 11 1969-12-31 16:00 Pie
kean@pesmerga:~/Desktop/new2$ cat Pie 
I like pie

---

### Post by ajgreeny on 2009-04-20
Presumably no permissions means no exclusion of any users to do what they want, 777?  Interesting one though.  Like you, I would expect it to be the opposite way round, ie, nobody can do anything.

---

### Post by Rujiel on 2009-04-20
0777 means everyone has every privilege.

---

### Post by ajgreeny on 2009-04-21
Yes, I realise that 0777 means anyone can do anything, hence my comment "Presumably no permissions means no exclusion of any users to do what they want, 777?"

---

