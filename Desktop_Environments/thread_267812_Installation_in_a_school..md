---
title: "Installation in a school."
date: 2006-09-29
forum: Desktop Environments
---

### Post by Nevermore on 2006-09-29
Hi everyone
i am planning to install ubuntu into the computers available to students in my university.
in order to do that i need some changes to be made:

games should be removed so that the computer are not always busy by ppl playng majohng.

possibility to install-remove program should be void, as long as possibility to make major system changes

flash plugin should be removed (yes, they play also online games) and maybe java too (if it doesn't cause too many browsing problems)

the user should have no rights to shutdown the system, mount or umount remote directory or browse the intranet.

That's all :D
how can i do it?
i am using Edgy beta 
Thanks

---

### Post by Perfect Storm on 2006-09-29
Firstly you might not use Edgy yet for working computers at the school, wait to it's stable.


Removing games:
```
sudo aptitude remove gnome-games gnome-games-data
```


I don't think flash and hava are installed by default.

---

### Post by Nevermore on 2006-09-29
> **Artificial Intelligence said:**
> Firstly you might not use Edgy yet for working computers at the school, wait to it's stable.


Removing games:
```
sudo aptitude remove gnome-games gnome-games-data
```


I don't think flash and hava are installed by default.

thanks
but what about preventing user to change important settings or installing stuffs

---

### Post by Ravse on 2006-09-29
Users gain administrative permissions using sudo. It's defined in /etc/sudoers

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

It's a matter of removing the users from the admin group. If you want your users to be able to do some administrative tasks, you can define which commands are available using sudo. Check the sudo documentation.

---

