---
title: "[SOLVED] About su -"
date: 2008-12-19
forum: General Help
---

### Post by jyaan on 2008-12-19
I was just wondering about the command "su -".

The only difference between "su" and "su -" is that the latter starts a new shell, correct?

---

### Post by bibleman on 2008-12-19
> a hyphen can be used to invoke a login shell and assume the target user's complete user environment:

Thats straight from wikipedia. Basically if you don't use the hyphen then you won't get the correct environment for that user.

---

### Post by cdtech on 2008-12-19
> The only difference between "su" and "su -" is that the latter starts a new shell, correct?
From the man page:
> -, -l, --login
Provide an environment similar to what the user would expect had the user logged in directly.

Thats correct. Home directory

---

### Post by jyaan on 2008-12-20
Ah, so it's a new shell either way then, but with - you get the complete environment? I'm just wondering about what actually happens "under the hood", I suppose I could say.

Edit: Oh, so then it goes to the home directory. It would also load all the .bash* files too? Like .bashrc, for example.

---

### Post by cdtech on 2008-12-20
> **jyaan said:**
> Ah, so it's a new shell either way then, but with - you get the complete environment? I'm just wondering about what actually happens "under the hood", I suppose I could say.

Edit: Oh, so then it goes to the home directory. It would also load all the .bash* files too? Like .bashrc, for example.

No, you maintain your current bash, you just log into the users account. To switch users you would have to log out and log in as that user.

---

### Post by jyaan on 2008-12-20
```
su - :
&#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;su&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree

su :
&#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;su&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree

jyaan@ubuntu:~$ vi .bashrc 
jyaan@ubuntu:~$ su jyaan
Password: 
Hello Jyaan the great!
jyaan@ubuntu:~$ exit
exit
jyaan@ubuntu:~$ su - jyaan
Password: 
Hello Jyaan the great!
jyaan@ubuntu:~$

jyaan@ubuntu:~$ vi .profile 
jyaan@ubuntu:~$ su jyaan
Password: 
jyaan@ubuntu:~$ su - jyaan
Password: 
Hello Jyaan the semi-Great!
jyaan@ubuntu:~$ 

```

So a new shell is started under the current shell either way because .bashrc is being run, but .profile is only run with su -. Thanks for the info guys, exactly what I was wondering about. :)

---

