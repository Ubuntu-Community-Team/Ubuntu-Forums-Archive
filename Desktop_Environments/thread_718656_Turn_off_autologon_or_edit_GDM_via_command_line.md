---
title: "Turn off autologon or edit GDM via command line"
date: 2008-03-08
forum: Desktop Environments
---

### Post by liquidcable on 2008-03-08
How do I turn off autologon or edit my GDM settings via the command line?

---

### Post by fracturedmorals on 2008-03-08
To turn off autologin, go to System > Administration > Login Window.

There should be an option under the "Security" tab.


To edit GDM options via command line, open /etc/gdm/gdm.conf with your favorite editor and hack away.

```
sudo emacs /etc/gdm/gdm.conf
```

---

### Post by liquidcable on 2008-03-08
Thanks for the info on the GDM modification.  

On the autologon change, I don't have access to the GUI (Gnome or KDE); that is my I need to change it via the command line.

---

### Post by hyperair on 2008-03-08
I think it's more of editing the /etc/gdm/gdm.conf-custom file. gdm.conf only contains the default settings. gdm.conf-custom is what's configured manually. 

Also, emacs doesn't come with the default installation. You could use nano which does, and is rather simple to use too.
```
sudo nano /etc/gdm/gdm.conf-custom
```

---

### Post by liquidcable on 2008-03-08
I don't really like emacs, and I am very familiar with nano as I have come from using Gentoo for years.  Thanks for the info.

---

