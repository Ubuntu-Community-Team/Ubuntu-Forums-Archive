---
title: "Login Problem - HangUp"
date: 2005-09-29
forum: Desktop Environments
---

### Post by elin2004 on 2005-09-29
Good day …….. I need help im a newbie and decided to try Ubuntu! Its really super cool it can detect my network computer all of them and its already PlugNPlay cool! But I enjoyed it for just an hour! i install a new themes and it installed no sweat! But when I tried to use it (i logout it hangUp (error is corrupted themes!) then I rebooted but it keep stoping @ LogIn Screen how could i return to Ubuntus Default LogIn Screen (Human) and how would i unInstall the theme using a terminal i know im a newbie but i need to do it i need help ASAP please..............

---

### Post by brk3 on 2005-10-01
Use punctuation, I cant understand a damn thing you're saying! Try this:
CTRL+ALT+F1. This will bring up a terminal, login and type: 

rm -rf .*

This will reset all your settings and should fix the broken themes. You could look or you could edit your .gtkrc-2.0 file either but I dont have the time to explain about that. If you dont have to many custom settings made the above is fine, otherwise google on editing the above file.
When done type:
sudo reboot

---

