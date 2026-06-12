---
title: "WINE and a game"
date: 2006-06-01
forum: Gaming &amp; Leisure
---

### Post by frying_fish on 2006-06-01
Just a quick question to anyone who is proficient with WINE, I can manage to get some of my windows apps working (guitar pro, and origin [program needed for university work]) however, I am trying to installl Pro evolution soccer 5.  The installer fails when it gets to the language selection, as it is unable to find the languages, and copying across the folder from my windows partition (and the option file) results in when I try to run the executable for the game, it telling me that the game is not properly installed.

Does anyone have any idea how to force wine to install and run this game (I know it apparently works in cedega, but am trying to not have to pay for a subscription to a service for just one game).

Any help guys?

---

### Post by jon_z on 2006-06-01
hrm... Possibly try to make the cd's an ISO, in the terminal:  dd if=/dev/hdc of=/tmp/prosoccer-cd1.iso        thats assuming your cdrom is hdc..  after you make iso's of all of the cd's mount the following way:  sudo mount /tmp/prosoccercd.iso  /cdrom -o loop               in your winecfg... add to the drives /cdrom and under advanced options in the dropdown menu make sure it is selected as a cdrom, apply your changes..   wine /cdrom/setup.exe (assuming thats how you start your setup) then as it asks for cd's leave the base cd mounted, i.e.  you mount your first install cd, leave that mounted, mount the next cd right over that, then unmount that one once your done with it, leaving that first cd mounted)   hopefully this will get around it..

---

### Post by frying_fish on 2006-06-01
Luckily its only the one dvd, so, will try it again as a mounted image, although I think I tried that before and didn't have much luck, will try it again though to see if it has changed.


EDIT:

Just tried that method, and unfortunately it still doesn't show any languages showing up, and as such the installer still fails, does anyone know how cedega manages to install it?

---

