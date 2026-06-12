---
title: "Gksudo problem"
date: 2005-02-15
forum: Desktop Environments
---

### Post by httpdss on 2005-02-15
On the instalation of ubuntu i created the "non root user" with password xxxxxxxx, some how, root got the same password. the problem is that when i changed the root password (from Gnome Users and Groups Menu), the password changed for the consoles tty[1-6] and for su too, but not for gksudo :-S 
any idea ??

---

### Post by benjamin on 2005-02-15
Sudo ... is not su.

---

### Post by Canguçu on 2005-02-15
[QUOTE=httpdss]On the instalation of ubuntu i created the "non root user" with password xxxxxxxx, some how, root got the same password. t[/QUOTE]

Sorry, you're mistaken here. 

Root is **disabled** by default when you install Ubuntu. "sudo" does not ask you the root password, but asks the **user password**. That way, logging directly as root (a very insecure behavior) is not allowed (because the true password of root is random). 

When you need to log as root to configure something, you should get into terminal and use "sudo" or use "gksudo" (which also asks for the **user** password).

The default user can do this because he's in the "sudoers" file. Please read more about this topic on the [Ubuntu Wikipage](http://www.ubuntulinux.org/wiki/RootSudo). If you prefer, you may change this.

---

### Post by benjamin on 2005-02-15
gksudo ask for the password of the user that launch it ..... that must be in /etc/sudoers.

---

### Post by httpdss on 2005-02-16
[QUOTE=httpdss]On the instalation of ubuntu i created the "non root user" with p***word xxxxxxxx, some how, root got the same p***word. the problem is that when i changed the root p***word (from Gnome Users and Groups Menu), the p***word changed for the consoles tty[1-6] and for su too, but not for gksudo :-S 
any idea ??[/QUOTE]
 Thx. Problem solved ...

---

