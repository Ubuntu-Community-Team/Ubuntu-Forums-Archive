---
title: "problem in applying -e in gnome-terminal"
date: 2007-04-17
forum: Desktop Environments
---

### Post by daziplqa on 2007-04-17
Hi all,
I have a program that run in command that i want to make a luncher for it.
this program called psql ( the name is not so important)

in the lunchar i wrote :
gnome-terminal -e psql -t pql 

but it just show me the gnome-termial for 1 second and then it get closed. 
is my options is invalid, please help.

---

### Post by thelinuxguy on 2007-04-17
> **daziplqa said:**
> 
gnome-terminal -e psql -t pql 


Issuing this command from another terminal itself should give you a clue about the error. Can you post the output?

---

### Post by daziplqa on 2007-04-17
No such error, try it your self. just it opens for 1 second and then the new termianl disappears.

---

### Post by thelinuxguy on 2007-04-17
> **daziplqa said:**
> No such error, try it your self. just it opens for 1 second and then the new termianl disappears.

I don't have psql installed. But your command doesn't produce an error on my system either. But it seems that the -e option causes gnome-terminal to execute the application and exit. I tried gnome-terminal -e nautilus and it did the same. To make it stay after executing the command, edit the default profile (or create a new one).

Start a terminal.
Edit >> Current Profile >> Title and Command >> When command exits: 
Change the option to "Hold the terminal open"
Close the terminal and launch your shortcut.

Does this work for you?

---

### Post by daziplqa on 2007-04-17
yes it does.
thanx toooooooooo much.
is this will affect any thing else ?

---

### Post by thelinuxguy on 2007-04-17
> **daziplqa said:**
> is this will affect any thing else ?

This will be the default behavior for gnome-terminal from now on. If you don't like this, create a new profile and modify the settings in that profile. Then when you launch gnome-terminal you can choose which profile to be used.

man gnome-terminal

lists many options that you have with profiles.

---

