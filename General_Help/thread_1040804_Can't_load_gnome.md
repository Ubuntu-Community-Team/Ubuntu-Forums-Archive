---
title: "Can't load gnome"
date: 2009-01-15
forum: General Help
---

### Post by beattyml1 on 2009-01-15
So I recently installed ubuntu on a new computer for my sis (P4@1.4GHz, 768MB, 80GB,  dell optiplex) and it will not load gnome I get to the ubuntu login screen and then why I try to log in gnome will not load, it does not seem like failsafe gnome is working either although I haven't given that as much time to see for sure.  What does work is the failsafe terminal, from there I am able to reconstruct a gnome like environment using:
```
metacity &
```
```
nautilus &
```
```
killall nautilus
```
```
gnome-panel &
```
for myself this might be ok but for my sis it is unacceptable, as she is not very technical, I'd really appreciate any ideas as this was my christmas present to her and I'd like to try to finish it before I go back to school

---

### Post by utnubuuser on 2009-01-16
Hi -- have you tried just re-installing "gnome-core"?  or how 'bout "sudo dpkg --configure -a", to try to re-configure anything that might be out of order.
xserver running ok? "sudo dpkg --reconfigure xserver-xorg".
Is xserver running? "sudo startx".

---

