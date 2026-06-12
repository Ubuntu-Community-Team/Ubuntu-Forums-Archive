---
title: "xmodmap doesnt do anything"
date: 2005-11-28
forum: Desktop Environments
---

### Post by maxtreiber on 2005-11-28
I have a 7-button mouse (3 for wheel and 2 click and 2 forward/backward)

Today i found out that, by using Protocol=ExplorerPS/2 in xorg.conf i can
actually use all of them :)

Unfortunately, Xorg thinks that my wheel are buttons 4 and 5, while they are
really 6 and 7, so i googled a little bit and found xmodmap but it doesnt do
anything, ever :(

for example, when i execute xmodmap -pp after booting he tells me that all 7
physical buttons are like the code button. Now i execute 
xmodmap -e "pointer = 1 2 3 6 7 4 5"
and xmodmap -pp shows me that the buttons are successfully switched.

BUT nothing in reality is changed. When i test it with Xev the ButtonPress events stay exaclty the same.

I tried simple stuff like xmodmap -e "pointer = 2 1 3 4 5 6 7", which should switch the right/left mouse-button, right ? still nothing changed ...

Do i have to activate something to get xmodmap to do anything ?

---

### Post by maxtreiber on 2005-11-30
since nobody is answering ...
could someone just try a

xmodmap -e "pointer = 3 2 1 4 5 6 7"

and tell if the buttons are really switched ?
i want to know if its my computer or its a breezy bug
-Thanks!!!

---

