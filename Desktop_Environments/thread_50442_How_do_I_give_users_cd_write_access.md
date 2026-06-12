---
title: "How do I give users cd write access?"
date: 2005-07-20
forum: Desktop Environments
---

### Post by MikeyXX on 2005-07-20
K3b will only work when you run it as root: sudo. How do I give a user write privs?

---

### Post by msh on 2005-07-20
[QUOTE=MikeyXX]K3b will only work when you run it as root: sudo. How do I give a user write privs?[/QUOTE]
 Try [http://www.ibiblio.org/pub/Linux/docs/HOWTO/CD-Writing-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/CD-Writing-HOWTO)

---

### Post by MikeyXX on 2005-07-20
[QUOTE=msh]Try [http://www.ibiblio.org/pub/Linux/docs/HOWTO/CD-Writing-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/CD-Writing-HOWTO)[/QUOTE]

Thanks. It said that it's not the device that you are giving the user rights to, but the program that is doing the request to the device. So this would work for me...I'll try it next time I need to burn something:

which k3b      (this  is what tells you the path to the program)
chown root.root /usr/bin/k3b        (changes the ownership...to root again..wierd)
chmod 4111 /usr/bin/k3b             (gives users access to the k3b program)

---

### Post by Joeb on 2005-07-20
[QUOTE=MikeyXX]Thanks. It said that it's not the device that you are giving the user rights to, but the program that is doing the request to the device. So this would work for me...I'll try it next time I need to burn something:

which k3b      (this  is what tells you the path to the program)
chown root.root /usr/bin/k3b        (changes the ownership...to root again..wierd)
chmod 4111 /usr/bin/k3b             (gives users access to the k3b program)[/QUOTE]


You could also edit the menu entry and stick a gksudo in front of the k3b command.  That way, it will ask for a password and if the user is a sudoer, they can burn.  Of course, if you want people to burn but not be able to sudo, then this won't work.

Joeb

---

