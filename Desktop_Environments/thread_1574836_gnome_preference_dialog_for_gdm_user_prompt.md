---
title: "gnome preference dialog for gdm user prompt"
date: 2010-09-14
forum: Desktop Environments
---

### Post by timotheus2 on 2010-09-14
I have accomplished this before but have managed to forget, and cannot find an answer on-line. I know that it is possible because I have one Ubuntu 10.04 machine that is configured this way.

I want GDM to prompt the user to enter their username via a text field, and then a password, instead of displaying a list of users to choose from.

One way to configure GDM's appearance is to run the following from a terminal:
    gksudo -u gdm dbus-launch gnome-appearance-properties

If I remember correctly, there is a different dialog to run than "gnome-appearance-properties" that allows changing whether GDM prompts for a username or displays a list. But I do not know what it is.

---

### Post by sisco311 on 2010-09-14
Hi and welcome to the forums!

You have to set the value of the /apps/gdm/simple-greeter/disable_user_list gconf key to true.

To disable the user list, run:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list "true"
```

To (re-)enable the user list, run:
```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list "false"
```



Of course, if you wish, you can use gconf-editor (GUI) to set the value of the key:
```
gksu -u gdm dbus-launch gconf-editor
```

If the above command fails with a "Cannot open display" error, run:
```
xhost +SI:localuser:gdm
```
then try it again.

---

### Post by timotheus2 on 2010-09-15
Thanks. I found the application GDM2Setup (package python-gdm2setup).

The application has a checkbox on the first tab named "Display user list a login" that does what I want. I expect that the manual gconf entry would have worked also.

---

