---
title: "[SOLVED] No Gnome Desktop"
date: 2008-04-04
forum: Desktop Environments
---

### Post by lynwode on 2008-04-04
Hey,
I have just tried to start up Gnome for the first time and i get the logon screen and login fine. However after logging in I get taken to the terminal as the user I logged in as. There is no GUI. Anyone got an ideas as to where my GUI has disappered too?

---

### Post by linuxtoindia on 2008-04-04
what does it shows?

---

### Post by tamoneya on 2008-04-04
what happens when you try ```
startx
```

---

### Post by lynwode on 2008-04-04
If I run startx I get an authority error, user not autorised to run X server. So I guess a permissions thing. I a bit new to the whole X Server world. Where and how would one set the permissions?

---

### Post by linuxtoindia on 2008-04-04
i think you should to reinstall gdm
or try the live cd
or 

sudo dpkg reconfigure xserver-xorg

---

### Post by lynwode on 2008-04-05
hmmm. Tryied reinstalling GDM, same issue.

Tried "sudo dpkg reconfigure xserver-xorg" but get dpkg: need an action option.

I'm totally lost now. Anymore suggestions.

---

### Post by linuxtoindia on 2008-04-05
IN WINDOWS WE NEVER HAD SUCH ISSUES!
 
WELL TRY 
sudo dpkg reconfigure xserver-xorg
 
AFTER THAT WRITE STARTX
 
 
AFTER THAT WRITE 
GDM
OR REINSTALL GDM

---

### Post by lynwode on 2008-04-05
I have already tried both suggestions no joy, see previous post

---

### Post by lynwode on 2008-04-05
I needed to do apt-get install ubuntu-desktop.

---

