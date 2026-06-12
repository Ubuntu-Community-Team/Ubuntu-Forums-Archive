---
title: "Gnome Menu Editor Wont Start"
date: 2005-12-29
forum: Desktop Environments
---

### Post by rowck001 on 2005-12-29
Today I thought I would edit my applications menu and a task pane shows that the applet is starting but then the disk activity light stops and no menu editor displays. What have I done? :confused:

---

### Post by anil_robo on 2005-12-29
Open a terminal, and type **smeg** and press enter. THis should start the menu editor. If it doesn't, you probably have broken smeg package. To repair it, remove smeg by using this command:
```
sudo apt-get remove smeg
```
and install it again
```
sudo apt-get install smeg
```.
This should solve the problem.

PLease let me know what happened. Ok? :)

---

### Post by manicka on 2005-12-29
I'd suggest using Synaptic and using the complete removal option. This will remove any faulty config files etc.

---

### Post by anil_robo on 2005-12-29
[quote=manicka]I'd suggest using Synaptic and using the complete removal option. This will remove any faulty config files etc.[/quote]
Good idea. But can't we do the same through commandline? I don't know the command though, if someone could tell me! :)

---

### Post by manicka on 2005-12-29
[QUOTE=anil_robo]Good idea. But can't we do the same through commandline? I don't know the command though, if someone could tell me! :)[/QUOTE]
sudo apt-get --purge remove smeg

---

