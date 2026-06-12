---
title: "every now and then screen remains black."
date: 2009-03-11
forum: General Help
---

### Post by the666pack on 2009-03-11
hello,

i know it is a difficult problem:

intrepid ibex
acer aspire 1692 laptop

every now and then (about 10% of overall boot count) the screen remains black. this means the bootup works fine til the x server starts and then i wait and wait for the gdm login screen but nothing happens. also power restart button or strg-alt-del as well as other keys dont seem to work anymore. the only thing that helps then is to switch power off and on :(

thats not a nice thing to kill linux. so anyway i already searched

dmesg

and 

/var/log/messages

but i didnt find anything suspicious. can someone maybe point me to some more log files where i might find the reason for the behaviour (e.g. x-server logs)?

thanks for helping,

j

---

### Post by geirha on 2009-03-11
You find the xserver logs in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old for the previous run.

When you hit the black screen. Does Ctrl+Alt+F1 get you to a console?

---

### Post by the666pack on 2009-03-11
i also tried this. dont get no console either.

in the xserver logs that i searched sofar i just got WW warnings no errors. so i think i have to wait til this problem occurs again

thanks for helping.

---

