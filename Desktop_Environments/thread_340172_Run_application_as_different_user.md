---
title: "Run application as different user"
date: 2007-01-16
forum: Desktop Environments
---

### Post by perlmonger on 2007-01-16
I'd like to know how to run an application as a different user. I don't want to run the application as root, I just want to be able to launch the application (GUI) as a different user. If I'm logged in as "fred" for example, I want to run the application as "editor" or some such. I'm thinking that there is a file such as this.desktop or something that I could edit to do this but I don't really have a clue. Any help would be appreciated. I've googled every combination of search terms I could think of but I can only find suggestions for running an app as root.

---

### Post by aysiu on 2007-01-16
Hm.

From the terminal, you can do ```
su editor
this
``` That's two commands, though. Maybe you could make a script out of it?

---

### Post by perlmonger on 2007-01-16
Yeah, I've done that. What I'd really like to do is set up the gnome menu item for this program so it runs the application as a certain user every time. 

Thanks for the idea though.

---

### Post by x1a4 on 2007-01-17
> **perlmonger said:**
> Yeah, I've done that. What I'd really like to do is set up the gnome menu item for this program so it runs the application as a certain user every time. 

Thanks for the idea though.

*gksu [-u <user>] [options] <command>*

Options in [] are optional, although to run as a user other than root the -u option is necessary. 

Run *man gksu* for more info.

---

### Post by perlmonger on 2007-01-18
Thanks for the tip! I've just recently discovered gksu and am trying it out. As it turns out, I can accomplish what I ultimately want by manipulating file permissions properly. I was being a bone-head and wasn't thinking the problem through.

Thanks everyone for the help

---

### Post by abc_user on 2007-01-18
I've tried to use gksu to run things as another user and have had X windows permission problems.  I started a thread here, [http://www.ubuntuforums.org/showthread.php?t=340721]("http://www.ubuntuforums.org/showthread.php?t=340721") ,
I'd appreciate any help.

---

