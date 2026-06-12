---
title: "System wide sudo effect?"
date: 2006-02-23
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-23
Hey.  I was wondering if there's a command that will make me a super user temporarly for all running apps so that I can save whatever file I want in whatever directory, etc.  For example, I ran gimp from the menu and came to save my pic in /usr/share/pixmaps.  Access denied.  So I had to save it to the desktop, then open nautilus with sudo and then copy it over.  Is there a way to login as su and just save the file directly?

---

### Post by lawngn0mex on 2006-02-23
[quote=FIONEX]Hey.  I was wondering if there's a command that will make me a super user temporarly for all running apps so that I can save whatever file I want in whatever directory, etc.  For example, I ran gimp from the menu and came to save my pic in /usr/share/pixmaps.  Access denied.  So I had to save it to the desktop, then open nautilus with sudo and then copy it over.  Is there a way to login as su and just save the file directly?[/quote]


```

sudo su -

```

that'll log you in as root.

to get out of it type exit and hit enter.

---

### Post by newuser111 on 2006-02-23
or just run gimp with gksudo gimp

that seems to be the most reasonable solution

---

### Post by FIONEX on 2006-02-23
I don't think you understand what I meant.  Say gimp is already open and the picture is ready to be saved.  I just remembered that I'm not logged in as root or I didn't launch gimp using sudo.  Can't I do something from there so that even the apps that are already open will have all permissions??

---

### Post by nanotube on 2006-02-23
fionex: no, you cannot. once a process is running without root permissions, there is no way to give it root permissions.

---

### Post by FIONEX on 2006-02-23
Back in the day when I use to use red hat, when something didn't have permissions, it would ask for root password.  That's why I was wondering.  But just another quick question.   Say I want to start something from the gnome menu (because I'm a noob and I don't know the command for it).  Can I log in as root in the terminal and then start the app from the menu (and it gets root permissions) somehow?  Just a hypothetical situation.

---

### Post by ardchoille on 2006-02-23
sudo mv /path/to/filename.ext /usr/share/pixmaps

Learning how to operate on the command line is a good thing ;)

---

### Post by heimo on 2006-02-23
[quote=FIONEX]Can I log in as root in the terminal and then start the app from the menu (and it gets root permissions) somehow? [/quote] 
It's not neccessary to log  in as a root, ever. Some people still insist doing this and it is possible (this forum has instructions how to do it). If you need to know command to launch any of those programs in the menu, right click on "Applications", select "Edit menus", find the application, right click, select properties. There you have Command-line with the command that gets executed when you click on the item. Then you can use [gksudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo") to launch only this application as a root.

It's rarely if ever neccessary to run any of those programs as a root. All the programs that need root access are already configured to ask your password to use gksudo (to use root access), those programs are in System->Administration. My advice is to not run any user applications as a root, it's bad practise and makes your system less secure.

---

