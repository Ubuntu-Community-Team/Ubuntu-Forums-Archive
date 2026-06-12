---
title: "Problem with sudo and NOPASSWD"
date: 2006-03-06
forum: Desktop Environments
---

### Post by 123dfdfg43 on 2006-03-06
Hi guys,

I was trying to set up a **sudoers** rule for my normal user, when I noticed that **NOPASSWD** option doesn't work. Here's the example:

sudoers
```

User_Alias      ANDREA = andrea
Runas_Alias     ROOT = root
Cmnd_Alias      FS = /usr/sbin/firestarter

ANDREA          ALL = (ROOT) NOPASSWD: FS

```

When I type the command, sudo ask for password:

```
andrea@localhost:~$ sudo /usr/sbin/firestarter
Password:

```

With option *Defaults  !authenticate* sudo doesn't ask for password anymore for any command, but it's a dangerous solution, isn't it?

I've already googled it, read the f*****g manual, but it doesn't work. Rules are surely correct.

Can it be a sudo bug?

Bye

---

### Post by dcstar on 2006-03-06
[QUOTE=andrea.ballatore]
.......
I've already googled it, read the f*****g manual, but it doesn't work. Rules are surely correct.

Can it be a sudo bug?

Bye[/QUOTE]
Did you use "visudo" to make the changes?

It checks the syntax to make sure that you have it correct.

---

### Post by 123dfdfg43 on 2006-03-06
[QUOTE=dcstar]Did you use "visudo" to make the changes?

It checks the syntax to make sure that you have it correct.[/QUOTE]

Yes, of course. Syntax is correct, I'm totally sure.

---

### Post by bradleyd on 2008-01-26
Did you ever get it to work?

---

