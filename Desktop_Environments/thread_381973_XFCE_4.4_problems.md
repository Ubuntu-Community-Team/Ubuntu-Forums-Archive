---
title: "XFCE 4.4 problems"
date: 2007-03-11
forum: Desktop Environments
---

### Post by jhhoward on 2007-03-11
I recently read about XFCE 4.4 and its new features so I thought I would give it a try. I usually use the GNOME desktop environment so I decided to install the xubuntu desktop.
I added the following repository to my sources.list:
deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0

then did 'sudo apt-get update' and then 'sudo apt-get install xubuntu-desktop'

All went smoothly and everything was installed, I can now log in with an XFCE session. I just have a few problems.

1) The new xfce desktop isn't loaded by default but the nautilus one is there
I fixed this by going to the settings and clicking the 'allow xfce to manage the desktop' but I still have to do this every time I log in, even if I save my session.

2) The new xfce desktop doesn't show the main system folders, i.e. Computer, Trash, etc

3) I can't get thunar to run from a menu properly. I miss my 'places' menu from gnome so I attempted to create a similar menu in xfce. I set the command to 'thunar ~/' for my home folder, but clicking it does nothing. The same command typed from a console works fine.

I quite like thunar as a file manager, its neat and simple. Is there any way I can use it as my default file manager in the GNOME environment?

Thanks,
James

---

### Post by seshomaru samma on 2007-05-15
I ran into the same problems and solve it by adding these commands to the startup:
```
killall nautilus
xfdesktop
```

if you have problems with thunar -write the whole path
```
thunar /path/to/wherever
```
works for me

Computer is just '/' as far as I remember
and Trash is a hidden file in your home directory

---

### Post by onbongos on 2007-05-15
i am using [http://goodies.xfce.org/projects/panel-plugins/xfce4-places-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-places-plugin) with no problems

---

