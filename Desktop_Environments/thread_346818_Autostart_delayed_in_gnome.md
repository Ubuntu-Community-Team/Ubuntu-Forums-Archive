---
title: "Autostart delayed in gnome"
date: 2007-01-26
forum: Desktop Environments
---

### Post by SPENEN on 2007-01-26
Hey.

I just installed beryl, but when I restarted my computer and logged in to gnome none of my autostart program's started.. Then after like 5 minutes all the programs starts.

I know the error can be caused by many different things but maybe you could point me to where I can see what gnome is doing at that time? Maybe a log-file or something.

Maybe gnome is waiting for a program to execute or something?

Thanks in advance.

---

### Post by wh0rd on 2007-02-07
This worked for me in autostarting beryl-manager and other applications:

*create a folder named "**autostart**" in the **.config** folder located in your home directory if it doesn't exist. (Ctrl+H to show hidden files, because any file/folder with a . in front of it is a hidden file/folder) 

For beryl-manager (as an example):
terminal:

```
gedit ~/.config/autostart/beryl-manager.desktop
```

Paste this into it:

```
[Desktop Entry]
Name=beryl-manager.desktop
Encoding=UTF-8
Version=1.0
Exec=beryl-manager
X-GNOME-Autostart-enabled=true

```

Save and close.
Now you should see a file named beryl-manager.desktop in the autostart folder, thats what autostarts beryl-manager. You can use this for almost any type of application you want to autostart after a Gnome login.

---

