---
title: "Feisty - Gnome doesnt start automatically"
date: 2007-05-05
forum: Desktop Environments
---

### Post by aprominax on 2007-05-05
I've got a problem, :(

suddenly, gnome doesn't startup automatically. 
Im using ubuntu feisty, intel pentium D, nvidia graphics card. Everyting is just working normal.
At startup: grub, ubuntu -> ubuntu loading screen(its nice btw :) ), and then a command line login, no error messages or anything like that. When i login, simply use "startx" to start gnome, dont see any errors or something. .. How do i get gnome or the login screen back ?? :confused:

---

### Post by ifross on 2007-05-05
Hmm, you could try 
```
sudo dpkg-reconfigure gdm
```

And then reboot

---

### Post by aprominax on 2007-05-07
Thnx ;) , 

oh, i had a few days holiday, so im a bit late :roll: 
but it works, thnx for it :).. really dont know what was wrong with gdm, hadn't changed anything, but its working now, thnx.. ( hadn't i said that yet :) )..

Aprominax

(srry for my bad English, if it's bad.. im trying, but dont think its very good, hope you understand it :D )
.. and may be closed now, problem fixed

---

