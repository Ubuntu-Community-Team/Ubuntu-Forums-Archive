---
title: "Permisson Denied!"
date: 2006-01-05
forum: General Help
---

### Post by antubis on 2006-01-05
When I tried to save a document from Quanta to /var/www/*, Quanta returns " ... permission denied". So I logon with the roor acount and change the permission with mc to "write by others", but now I can write in /var/www/ but I can`t in subdirectories. How can I change chmod of directory and its subdirectories.

10x

---

### Post by Maggot on 2006-01-05
[QUOTE=antubis]When I tried to save a document from Quanta to /var/www/*, Quanta returns " ... permission denied". So I logon with the roor acount and change the permission with mc to "write by others", but now I can write in /var/www/ but I can`t in subdirectories. How can I change chmod of directory and its subdirectories.

10x[/QUOTE]
I'd advise against it but:

chmod XXX -R /var/www

XXX = the permissions you want.

---

