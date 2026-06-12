---
title: "Super User"
date: 2008-12-23
forum: General Help
---

### Post by gramsyn on 2008-12-23
I would like to take super user benefits. How can I do it? su and then password is not working

---

### Post by albinootje on 2008-12-23
> **gramsyn said:**
> I would like to take super user benefits. How can I do it? su and then password is not working

Did you try sudo ?
Ubuntu uses sudo exclusively, and with that root login is not possible by default.
In other Linux distributions like Fedora the old-fashioned su (and root login) is used by default.

See also : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gramsyn on 2008-12-23
sudo is not working by its own. It requires an extension.
I would like to open a file, edit it and save it. The system doesn't let me save it, so I thought I should be superuser. How can I edit it using sudo?

Thanks

---

### Post by redilyn on 2008-12-23
If you are working from the terminal you can try the following it may help

```

sudo -s

```

---

### Post by kerry_s on 2008-12-23
> **gramsyn said:**
> sudo is not working by its own. It requires an extension.
I would like to open a file, edit it and save it. The system doesn't let me save it, so I thought I should be superuser. How can I edit it using sudo?

Thanks

in gui:
**gksu gedit /path/to/file**

in terminal/console:
**sudo nano /path/to/file**

---

### Post by gramsyn on 2008-12-23
Ok. I gave the nano command and edited the file. How do I save???

---

### Post by redilyn on 2008-12-23
i think it is CTRL+X then press Y for yes

---

### Post by albinootje on 2008-12-23
> **gramsyn said:**
> Ok. I gave the nano command and edited the file. How do I save???

ctrl-x is to exit in nano, after that it will ask you for a confirmation for saving the file.

---

### Post by gramsyn on 2008-12-23
Thanks very much

---

