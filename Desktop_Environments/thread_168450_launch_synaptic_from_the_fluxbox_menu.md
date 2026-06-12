---
title: "launch synaptic from the fluxbox menu?"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Choad on 2006-04-30
i could launch it from a terminal with sudo synaptic, but when i try and launch it from the menu, it (correctly) tells me i need to run it as root.

how can i fix this?

im new to flux, hope its ok to post in this forum, there isnt a fluxbox section. (there should be tho)

---

### Post by Choad on 2006-04-30
well, i installed gnome-sudo and changed the menu entry to 

[exec] (Synaptic) {gksudo synaptic}

the sudo box comes up, but then when i type my password (and here im not sure if its gksudo saying this or synaptic) it comes up with

failed to run synaptic as root user
unable to copy the user's xauthorisation file

so actually now i read it again it sounds like gksudo is having the problem. any clues as to how to solve?

---

### Post by Choad on 2006-04-30
ahhh well wasnt this fun

for reference: gotta change the ownership and group of the .Xauthority file

it was owned by root because it was created with a sudo command at some point

sudo chown richard:users ~/.Xauthority

---

