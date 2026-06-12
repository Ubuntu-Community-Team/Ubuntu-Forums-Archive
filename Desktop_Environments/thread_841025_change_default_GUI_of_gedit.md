---
title: "change default GUI of gedit"
date: 2008-06-26
forum: Desktop Environments
---

### Post by pdah on 2008-06-26
I installed the theme for Ubuntu last month. And obviously it applied to all the application included gedit.
Now when I use the command "gedit" the GUI is different from "gksudo gedit". 
I know that it's because the configuration for gnome of root user is diffenrent from the other users.

What I want is to use the gnome configuration of root only for gedit.
It means when I type "gedit", the GUI is the same as "gksudo gedit". Is it possible ?

Thanks in advance.

---

### Post by evozniak on 2008-06-26
sudo gnome-appearance-properties

change ROOT theme to same as your user.

---

### Post by Xgen on 2008-06-26
Aye...I don't know if you can single out only one non-root program to use a root theme.  Non-root programs use the .theme folder in your home folder and root ones use the root folder one. They both also share a common usr/share/theme folder. You can also modify the .gtkrc-2.0 file in either home/root folders or with Gnome Color Chooser. Would be interested to find out...

---

### Post by ingvildr on 2008-06-26
Just move the theme into /usr/share/themes so all users including root can use the theme.

---

### Post by mcduck on 2008-06-26
Just create symbolic links from your own themes directory to root's theme directory. This way root's apps will automatically always use the same theme that you are using.

```
sudo ln -s /home/username/.themes /root/.themes
sudo ln -s /home/username/.icons /root/.icons
```

Doing it the other way, making your Gedit use root's theme, is not that simple thing to do.. I know there is some way to launch a program and define the GTK theme it should use but I've never found out how to actually do it..

---

### Post by pdah on 2008-06-26
Thanks for your reply. Anyway, I want to keep the default theme when I run the apps as root, and see the customize theme if I run them as normal user.
There is only one exception for gedit, because i'm using gedit as an IDE and it's not looking good in the customize theme.

---

