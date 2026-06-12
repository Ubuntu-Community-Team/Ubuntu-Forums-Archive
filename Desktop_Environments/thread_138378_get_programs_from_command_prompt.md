---
title: "get programs from command prompt"
date: 2006-03-01
forum: Desktop Environments
---

### Post by billh1241 on 2006-03-01
I was only able to do a basic install and after logging in I get a black screen with my login name@ubuntu~$.  How do I go from there and get some programs loaded.  I have a 6.5G hdd with 5G free.  Thanks, as you can tell I am new and dumbber than dirt.

---

### Post by knalle on 2006-03-01
like if you want **elinks** you write:

```
sudo apt-get install elinks
```

to install the **kde desktop** write:

```
sudp apt-get install kubuntu-desktop
```

etc

---

### Post by billh1241 on 2006-03-01
thanks for the help so quickly. I will do that right away.  thanks again. Bill

---

### Post by Sutekh on 2006-03-01
How come you could only do a basic (server?) install?  This is a pretty open-ended question, so I'm gonna wing it.  See what you think.

To install programs from the command line, use **apt-get**

Basically it takes the forms ```
sudo apt-get install packagename
```

But first, do you want a graphical desktop environment?  GNOME? KDE? XFCE?

Have a look at this site, and click on the Desktops at the bottom for some screenies on these environments, and maybe you can decide what you want.

[http://xwinman.org/]("http://xwinman.org/")


If you want [GNOME](www.gnome.org) - Default Ubuntu Desktop, I'd use this command
```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.

If you want [KDE](www.kde.org) - Most Common Linux Desktop, I'd use
```
sudo apt-get install kubuntu-desktop
```

If you want [XFCE](xfce.org) - very light desktop, I'd use
```
sudo apt-get install xubuntu-desktop
```

These commands will install the respecitve desktops with most of the basic programs you will need.

---

