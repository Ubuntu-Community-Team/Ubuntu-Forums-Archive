---
title: "login window"
date: 2011-01-29
forum: Desktop Environments
---

### Post by raunhar on 2011-01-29
While installing Lubuntu 10.04, I opted for Auto login, but now I want to go for it.
How can I restore that option, so that I get the login window on start up.

---

### Post by hictio on 2011-01-29
Try this:

System > Administration > Login Screen

You'll have to type your password to unlock the options, and then, un-check the option:

"Log is as" ..... "automatically"

Hope this helps.

---

### Post by SteveDee on 2011-01-29
> **raunhar said:**
> While installing Lubuntu 10.04, I opted for Auto login, but now I want to go for it.
How can I restore that option, so that I get the login window on start up.

On Lubuntu 10.10 you have to edit the /etc/xdg/lubuntu/lxdm/lxdm.conf file (I think its the same on 10.04).

To auto login the start of this file should be like this:-
```

[base]
autologin=raunhar

```
...or to switch off autologin add a # like this:-
```

# autologin=raunhar

```

---

### Post by raunhar on 2011-01-31
How to edit the file.
Terminal is not accepting the command sudo gedit

---

### Post by SteveDee on 2011-01-31
> **raunhar said:**
> How to edit the file.
Terminal is not accepting the command sudo gedit

Are you sure you have gedit installed? I do not have 10.04, but on 10.10 the default text editor is "leafpad". So  you should either do:-
```

sudo leafpad

```
...or more correctly:-
```

gksu leafpad

```

---

