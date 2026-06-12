---
title: "Running a program as root on startup"
date: 2006-03-25
forum: Desktop Environments
---

### Post by 4tro on 2006-03-25
my first post on this forum will be a question :p 

i need some help with running a program as root on startup

the problem is that this program will use port 411 to run and runs using wine...

i tried to edit the sudoers file but was not succesful in getting this to work

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification


# Cmnd alias specification
Cmnd_Alias	REDI = /usr/bin/wine /home/quattro/ynhub-winetest/YnHub.exe

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
quattro	ALL= NOPASSWD: REDI

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

but for some reason when i try to run 
quattro@quattrolap:~$ sudo wine /home/quattro/ynhub-winetest/YnHub.exe
it still asks for my password

can anybody explain me what i'm doing wrong?](*,)

---

### Post by akshaysrinivasan on 2006-03-25
try going to System>preferences>sessions in the gnome panel.click on the sessions tab and add the startup programs with the commands

---

### Post by akshaysrinivasan on 2006-03-25
Try going to System>preferences>sessions in the gnome panel .click on the startup tab and add the commands along with gksudo.

---

### Post by 4tro on 2006-03-25
problem is that i won't be present at the pc while this is taking place... so i can't type in the pass. the computer on which this is going to run won't even have a monitor to see where i'm typing ^^ :P
so the sudo shouldn't ask for a password for this specific command

---

### Post by Hairy_Palms on 2006-03-25
you can do it like this
> echo  "yourpasswordhere"  | sudo -S yourcommandhere

---

### Post by 4tro on 2006-03-27
where should i do that?
because placing it in startup doesn't seem that secure

---

### Post by mdmarmer on 2006-03-27
The first answer in this FAQ makes it fairly clear ....

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)
that is,
How can I get Firestarter to load automatically when I log in as a regular user?


Mike

---

### Post by 4tro on 2006-03-27
thanks looks like that one could work i'll try tommorow =)

---

### Post by 4tro on 2006-03-28
looks like that did the trick, but i will try it on my next server reboot =)

---

### Post by 4tro on 2006-03-29
looked like this could work.... but it doesn't. It starts complaining about using the wrong display or absence of my x server. I suspect it has something to do with the sudo command not being able to start a graphic wine application...
any suggestions? I will start it manually for now

---

