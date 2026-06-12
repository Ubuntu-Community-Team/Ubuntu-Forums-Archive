---
title: "Not loading.."
date: 2006-05-24
forum: Desktop Environments
---

### Post by YaNoS on 2006-05-24
Wierd bug with ubuntu, I seem not being able to get past the user and password inputing screen, I put in my user/pass, press OK, and Ubuntu should start loading but all I get is that orange screen and it doesn't load up, no apps, no icons, no nothing.

Anyone knows what could cause this?

---

### Post by nanotube on 2006-05-24
did it use to work before, but now suddenly doesnt, or is that the behavior as soon as you installed?

---

### Post by YaNoS on 2006-05-24
It used to work before, it adopted this strange behavior just recently

---

### Post by nanotube on 2006-05-24
installed any packages recently? fiddled around with the firewall?

---

### Post by YaNoS on 2006-05-24
[QUOTE=nanotube]installed any packages recently? fiddled around with the firewall?[/QUOTE]


the most recent package is probably aMSN, didn't touch the firewall =(

Althought I did update my system before that happened

---

### Post by nanotube on 2006-05-24
[QUOTE=YaNoS]the most recent package is probably aMSN, didn't touch the firewall =(

Althought I did update my system before that happened[/QUOTE]
hmm, well, at least it didn't happen without you doing anything at all. :)
well, one thing you can try is to turn off the gui completely (ctrl-alt-f2 to switch to another console, and type "sudo /etc/init.d/gdm stop") and then start it from that console, using "startx" and see if you get any error output.

another thing to try if that doesnt do anything fruitful, is to back up and move your ~/.gnome2 folder and see if that solves it (mv .gnome2 .gnome2-backup), then restart.

---

### Post by YaNoS on 2006-05-24
[QUOTE=nanotube]hmm, well, at least it didn't happen without you doing anything at all. :)
well, one thing you can try is to turn off the gui completely (ctrl-alt-f2 to switch to another console, and type "sudo /etc/init.d/gdm stop") and then start it from that console, using "startx" and see if you get any error output.

another thing to try if that doesnt do anything fruitful, is to back up and move your ~/.gnome2 folder and see if that solves it (mv .gnome2 .gnome2-backup), then restart.[/QUOTE]


Wow thanks, i'll try that then reply

---

