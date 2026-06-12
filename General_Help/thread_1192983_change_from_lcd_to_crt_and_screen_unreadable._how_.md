---
title: "change from lcd to crt and screen unreadable. how to fix"
date: 2009-06-20
forum: General Help
---

### Post by stinger30au on 2009-06-20
today i finished moving my kids pc to their room
i set it up on my 17 inch lcd monitor and all was good

when i moved it to the kids room and plugged in their crt the screen looked like the resolution was very low and was almost unreadable

i could not read the screen that said login or password
but i typed them in anyhow and got to the desktop

the desktop was readable but still to low

when i tried to run system preferences and display and change the screen resolution and exit it would keep saying it could not modify the x11.org file

so heres the fix

right click applications

click edit menus

click preferences

right click display

click properties

find the command and it will say

gnome-display-properties

you need to put infront of this gksudo so it looks like this

gksudo gnome-display-properties

now click ok and exit

*NOW* you can run system , preferences, display


it will ask you for the password, type it in

make the screen adjustments and click save

this time you will see no erros come up

logout or restart pc and your good to go!

hope this helps someone

---

