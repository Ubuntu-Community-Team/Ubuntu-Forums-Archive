---
title: "Add Applications Menu Gone"
date: 2006-02-23
forum: Desktop Environments
---

### Post by naruto11111 on 2006-02-23
Hi, somehow I managed to delete the add applications menu button under system tools.  I was able to put it back on (minus the icon) but now when I try to use it, it prompts me for my password then gives me the following error:

Failed to run /usr/bin/gnome-app-install as user root:
Child terminated with 1 status


I don't want to kill anymore children but I want this button back.  Can someone tell me how to reinstall it?  Thanks in advance!

-Michael

---

### Post by aysiu on 2006-02-23
First of all, as I understand it, you just removed the button and not the application itself. Just to be sure, though, open a terminal and type ```
sudo apt-get update
sudo apt-get install gnome-app-install
```

Okay. If it's there, what's the command you put in for the menu launcher? Was it ```
gksudo gnome-app-install
```?

---

### Post by naruto11111 on 2006-02-23
I used /usr/bin/gksudo /usr/bin/gnome-app-install which was recommended by another forum member.  But the problem is fixed, it looks like i somehow removed the actual application.  

Reinstalling it worked, thank you very much!  =)

-Michael

---

