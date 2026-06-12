---
title: "Alacarte Menu Editor Not Functioning..."
date: 2006-06-02
forum: Desktop Environments
---

### Post by sardopsycho on 2006-06-02
I have read several threads indicating trouble with the Alacarte Menu Editor.  I have attempted to reinstall using Synaptic Package Manager, I have also gone as far as using sudo apt-get install menu-xdg through the terminal to no avail.

Is this feature just broken for now and an update later will come??  I would really like to customize my menus and get on with life lol.

](*,)

---

### Post by bluevoodoo1 on 2006-06-02
You could try the "other" menu editor...

```
smeg
```

Perhaps pasting here the output of "alacarte" from a terminal will give more ideas of what to fix?

---

### Post by sardopsycho on 2006-06-02
paul@morpheus:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 72, in __init__
    self.loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 205, in loadMenus
    self.sys_handler = MenuHandler('settings.menu', self.options)
  File "/usr/lib/python2.4/site-packages/Alacarte/PyXDGMenuHandler.py", line 36, in __init__
    os.makedirs(os.path.split(path)[0])
  File "/usr/lib/python2.4/os.py", line 159, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/home/paul/.config/menus'

paul@morpheus:~$ sudo su
Password:
root@morpheus:/home/paul# alacarte

(alacarte:20277): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

NOW the menu editor is running - I have admin privs, so I don't understand what is happening - I can launch it through the terminal, but I cannot launch it through the GUI under Applications -> Accessories -> Alacarte Menu Editor - nothing happens when it is clicked on.

---

### Post by sardopsycho on 2006-06-02
One more thing to add - 

Even though the Alacarte Menu Editor is running - no matter what changes I make, they are not taking.

---

