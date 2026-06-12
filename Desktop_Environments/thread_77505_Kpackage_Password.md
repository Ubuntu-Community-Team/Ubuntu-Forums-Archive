---
title: "Kpackage Password"
date: 2005-10-16
forum: Desktop Environments
---

### Post by AllenP on 2005-10-16
I've been using linux for around two days and ubuntu is my first distrubution. I installed Kpackage to try to get some applications easily installed. It works pretty good except when I go to finally install the programs it asks me for a password. I type in my password, but every time it denys me access. Do I have to type in anything else? Any help would be greatly appreciated.

---

### Post by Ampersand on 2005-10-17
Try running 
```
sudo kpackage
```
from a terminal. I've found that occasionally programs start asking for the root password instead of the sudo one when not initially run with administrator priveledges.

---

### Post by AllenP on 2005-10-17
Thanks, it worked perfect.

---

### Post by ironwoodcarver on 2005-12-03
:confused:  it dosn't work for me anything else I can do?????????????

---

### Post by aysiu on 2005-12-03
[QUOTE=ironwoodcarver]:confused:  it dosn't work for me anything else I can do?????????????[/QUOTE] You've got to be more specific than that. What did you try and what happened? If you got any errors, what were they?

---

### Post by Rinzwind on 2005-12-05
Hello,

What I did was 'edit item' (from the menu) and change the following: 

Before "kpackage " I added "sudo". So it changed into "sudo kpackage -caption "%c" %i %m %u".
And I tagged the "run in terminal".

What happens is that you get asked root password 1 time :)

---

### Post by ironwoodcarver on 2005-12-09
[QUOTE=aysiu]You've got to be more specific than that. What did you try and what happened? If you got any errors, what were they?[/QUOTE]

I tried sudo passwd and my own root password accepted by everything else but not in Kpackage I think I will stay with adept and uninstall Kpackage it appears that it just doesn't like me why would they have a package that wont recognize you I get no error messages just wrong password very odd. Every other package manager I have used does not have this prob. anyway thanks and to those that worked so hard on Kpackage try agian maybe it can be made to recognize a root password I don't know but you would think that for a package that would be the norm. :confused:

---

