---
title: ".xinitrc not doing anything"
date: 2005-03-31
forum: Desktop Environments
---

### Post by Ric_ on 2005-03-31
Hi all  I have created a .xinitrc file in my home dir because i want to eventually make ssh-agent pop up and ask me my ssh keyprase but it didnt work so i thought start simple and added the line 

xterm &

When i log into x nothing happens. Do i have to enable this file in the X config?

Cheers

---

### Post by alastair on 2005-03-31
X can be quite arcane and hard to trace sometimes. A lot of obscure setup and configuration ...

See : man xinit

You probably want to do something like :

- boot (you will see the login screen GDM probably)
- switch to a VT (CTRL+ALT+F1)
- login and stop GDM : sudo /etc/init.d/gdm stop
- create your ~/.xinitrc file e.g.

xterm &
gnome-session

- run : startx

Does this work?

---

