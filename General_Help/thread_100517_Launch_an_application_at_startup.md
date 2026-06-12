---
title: "Launch an application at startup"
date: 2005-12-07
forum: General Help
---

### Post by ad noiseam on 2005-12-07
Hello,

I would like to launch xbindkeys every time I start my KDM session. In Gnome, there is a small GUI application to specify this, but I can't find any equivalent in KDE. Moreover, my session is always ended up when I log out, and I have to enter "xbindkeys" in a terminal every time.

How could I set up this to start with every session?

Nicolas

---

### Post by aysiu on 2005-12-07
I'm not sure if this is exactly what you're looking for, but maybe you could save a session and have it start up every time you log in?

---

### Post by Zaventh on 2005-12-08
Just symlink the application to ~/.kde/Autostart

eg:

```
ln -s /usr/bin/xbindkeys ~/.kde/Autostart/xbindkeys
```

---

### Post by floyd27 on 2005-12-08
Could you or someone explain the steps in that code.. Im just wondering what it satnds for so i will understand whats going on a little better.I have used this to start up other things and it works great..
thanx

---

### Post by Joey French on 2005-12-08
Yes, I would like to know the steps as well. I want a few things to autostart, and gnome has a tool for it, but i want to use this method.

---

### Post by martamius on 2005-12-09
[QUOTE=Zaventh]Just symlink the application to ~/.kde/Autostart

eg:

```
ln -s /usr/bin/xbindkeys ~/.kde/Autostart/xbindkeys
```[/QUOTE]

KDE automaticaly runs anything in your ~/.kde/Autostart directory at startup.
```
ln
``` is the command to make a link.

the first argument ```
-s
``` tells it to make a symbolic link. then the second argument ```
/usr/bin/xbindkeys
``` tells it what to link to. In this case, its the xbindkeys program.


the third and final argument ```
~/.kde/Autostart/xbindkeys
``` is the name of the link(with path to it). In this case, the symbolic link is being put into the ~/.kde/Autostart directory, so that link will be executed at startup.

For more info on the ln command, do:
```
man ln
```

---

### Post by guice on 2005-12-09
Think of the *AutoStart* directory as KDE's version of Window's *Startup* directory. They both work exactly the same.

---

### Post by floyd27 on 2005-12-11
Great.. 
thanx guys.. very usefull info.....

---

### Post by berliita on 2007-12-22
And what about Gnome? How to launch an application at startup on Gnome?

---

### Post by berliita on 2007-12-22
Forum user ebash has answered my question in another thread, namely: 
[http://ubuntuforums.org/showthread.php?p=3996077#post3996077](http://ubuntuforums.org/showthread.php?p=3996077#post3996077)

---

