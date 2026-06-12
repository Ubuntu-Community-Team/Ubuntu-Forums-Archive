---
title: "allowing root user login - kubuntu"
date: 2005-06-14
forum: Desktop Environments
---

### Post by btumpps on 2005-06-14
hello ppl. i have set a password for the root with the command
sudo passwd root

but when i want to login with the user name "root" in kde (kubuntu) i get the message:
root login not allowed!

what should i do?

---

### Post by Takis on 2005-06-14
STF.
[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)

---

### Post by jeremy on 2005-06-14
Try going to Control Centre (as root ie. sudo ) -> System Administration -> Login Manager, then, on the 'user' tab 'Select Users and Groups', select root.

---

### Post by btumpps on 2005-06-14
[QUOTE=Takis]STF.
[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)[/QUOTE]

in that link it says
THEN, again from start menu go to System --> Administration --> Login Screen Setup. 

there's nowhere "login screen setup" in kubuntu. where can i do that in kde?

---

### Post by codejunkie on 2005-06-14
im not 100% sure but i think go to kcontrol and login manager i believe it will let you choose wether or not root is allowed to login through kdm but to change that you need root privledges so press alt+F2 and type kdesu kcontrol or you can hit ctrl+alt+F1 login as root and type startx hope this helps and let me know it this works.

---

### Post by btumpps on 2005-06-14
[QUOTE=codejunkie]im not 100% sure but i think go to kcontrol and login manager i believe it will let you choose wether or not root is allowed to login through kdm but to change that you need root privledges so press alt+F2 and type kdesu kcontrol or you can hit ctrl+alt+F1 login as root and type startx hope this helps and let me know it this works.[/QUOTE]

"kdesu kcontrol" worked thx a lot.

---

### Post by btumpps on 2005-06-14
[QUOTE=jeremy]Try going to Control Centre (as root ie. sudo ) -> System Administration -> Login Manager, then, on the 'user' tab 'Select Users and Groups', select root.[/QUOTE]

but there's another problem. i have selected "root" but when i want to login as root again i get the message "root login not allowed!"

---

### Post by codejunkie on 2005-06-14
if you installed ubuntu and added kde later through synaptic or sudo apt-get install kubuntu-desktop you might be using gdm insted of kdm.

---

### Post by btumpps on 2005-06-14
[QUOTE=codejunkie]if you installed ubuntu and added kde later through synaptic or sudo apt-get install kubuntu-desktop you might be using gdm insted of kdm.[/QUOTE]

nope i have installed kubuntu.

---

### Post by codejunkie on 2005-06-14
i can't remember right off hand how to change it. but if you really need root access you could try ctrl+alt+F1 login as root and type startx if it complains that x is already running just type killall kdm and then startx that should work. but i try and find out an easier way to do it through kdm for you.

---

### Post by btumpps on 2005-06-14
the problem has been solved.

 sudo kate /etc/kde3/kdm/kdmrc
 click the find button, enter "AllowRootLogin"
 change the value to "true"
 save, logout, log back in as ROOT!

---

### Post by desdinova on 2005-06-14
Logging into the gui as root is a SERIOUSLY bad idea - root is not a normal account - its asking for trouble logging in as root - is's a windowsism best un-learnt.

---

### Post by Takis on 2005-06-14
[QUOTE=btumpps]the problem has been solved.

 sudo kate /etc/kde3/kdm/kdmrc
 click the find button, enter "AllowRootLogin"
 change the value to "true"
 save, logout, log back in as ROOT![/QUOTE]

If you'll notice, that was actually in the link I sent you - buuut, I probably could have been a bit more specific. More help next time, I promise!

---

