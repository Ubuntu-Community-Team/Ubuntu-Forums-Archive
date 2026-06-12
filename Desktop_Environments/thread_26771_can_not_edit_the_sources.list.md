---
title: "can not edit the sources.list"
date: 2005-04-13
forum: Desktop Environments
---

### Post by lowell on 2005-04-13
:-) 

I cannot edit the sources.list on gedit because it is on the read only. how could i change it inorder that i could modify it.

---

### Post by dataw0lf on 2005-04-13
You have to have the correct permissions (i.e., 'sudo gedit sources.list' at the command line).  Alternatively, you can add them through synaptic.

---

### Post by Buffalo Soldier on 2005-04-13
Go to the console (command line interface) and type:```
sudo gedit /etc/apt/sources.list
```It will then ask you for a password. Just type in your user password and hit enter.

---

### Post by kal_zakath on 2005-04-14
Maybe it's a stupid question, bu why do you use gedit if you have kde ?? 

Imho Kate is a relly nice, powerfull and fully integred with KDE text editor, you should give it a try  ;)

However, it won't solve you problem, but as said above, it's a permission problem.

If you don't like to go in console to launch you text editor with root privileges you can use the kdesu command in the "run a command" dialog from the kde menu. 

with kate the command will be : kdesu kate 

and if you really want to stick with gedit : kdesu gedit 

You can even add a menu entry with one of these commands, i.e. in system menu, to have it avariable all the time.

---

### Post by srd on 2005-04-14
tape in console:
sudo apt-get install kedit
then :
sudo kedit /etc/apt/sources.list

---

### Post by kal_zakath on 2005-04-14
[QUOTE=srd]tape in console:
sudo apt-get install kedit
then :
sudo kedit /etc/apt/sources.list[/QUOTE]

:shock:

why would he do that ? there is already enough text editors installed, so I don't get the point to install another one, it has nothing to do with his problem  :roll:

---

### Post by srd on 2005-04-14
kate not working for me.
You can start with 
# kdesu kate /etc/apt/sources.list

---

### Post by srd on 2005-04-14
[QUOTE=dataw0lf]You have to have the correct permissions (i.e., 'sudo gedit sources.list' at the command line).  Alternatively, you can add them through synaptic.[/QUOTE]


kynaptic for KDE

---

### Post by knappen on 2005-04-15
Just right click on the file, under actions (I think) select "edit as root".

Works for me.

---

