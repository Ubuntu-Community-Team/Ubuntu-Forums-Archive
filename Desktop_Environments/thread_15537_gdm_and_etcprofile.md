---
title: "gdm and /etc/profile"
date: 2005-02-15
forum: Desktop Environments
---

### Post by kwisatz on 2005-02-15
I export some variables (like CLASSPATH) into /etc/profile. 
I have switched from text login to graphic login with gdm and now I can't see my variables!
with gdm /etc/profile is no more readed? 

I don't understand how /etc/profile works...
who reads it? 

Thank you in advance and sorry for my poor english,

Matteo

---

### Post by piedamaro on 2005-02-15
[QUOTE=kwisatz]I export some variables (like CLASSPATH) into /etc/profile. 
I have switched from text login to graphic login with gdm and now I can't see my variables!
with gdm /etc/profile is no more readed? 

I don't understand how /etc/profile works...
who reads it? 

Thank you in advance and sorry for my poor english,

Matteo[/QUOTE]
 It should work, you may try to export your variables in /etc/bash.bashrc instead, this is bash-specific, while profile should be a more general system profile.
Ciao :)

---

### Post by benjamin on 2005-02-15
I didn't understand if you want to define a variable in /etc/profile .... so every shell knows it .....   or you want to define a variable in a shell and make it visible to another ?

---

### Post by benjamin on 2005-02-15
I read piedamaro post ... it's true, but the file you have to edit is
~home/.bashrc

Ciao  :-)

---

### Post by benjamin on 2005-02-15
If you want the variables exported visible to all user export it in
/etc/bash.bashrc 
If you want it visible to you ... export it in
~home/.bashrc

Ciao

---

### Post by shmonkey on 2005-02-15
Yeah I've found the same thing, it seems /etc/profile is not used and you have to define global environmental variables in /etc/gdm/gdm.conf.

/etc/bash.bashrc etc. only work when you are running a program from the cli.

strange !!!

---

### Post by kwisatz on 2005-02-16
I put all my global environment variables in /etc/environment, 
now everything works :)

thank you for helping me,

kwisatz

---

