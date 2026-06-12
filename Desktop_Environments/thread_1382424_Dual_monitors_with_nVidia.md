---
title: "Dual monitors with nVidia"
date: 2010-01-15
forum: Desktop Environments
---

### Post by w1ll1am on 2010-01-15
okay so I decided that I wanted to try out dual monitors so I got an old one and hooked it one and booted into windows XP and set it up good to go. So I figured I would set it up in Ubuntu also and since it worked so well in windows I thought well it can only work better in Linux. This is not true. okay i have a dell flat panel hooked up as the primary monitor using my DVI input and a very old Hansol monitor hooked up to the VGA port on the same card. After reading for I while I did this

sudo nvidia-xconfig. 
gksudo nvidia-settings.
 
set up the monitors how I wanted and clicked apply then i clicked save to configuration file and clicked preview and copied it. Then I ran sudo gedit xorg.conf and pasted what I had copied. saved and restarted everything was looking good and then once I got in I had both monitors working but i had set up the Hansol to be to the left and it is to the right and the Dell is to the left. Also when i bring up the terminal for instance it is solid white i can not see anything i can type commands and them run so it is there it is a problem with the way i have the configuration set up but i do not know how to fix it so any help is appreciated.

---

### Post by w1ll1am on 2010-01-15
also if i had a different card would this work easier?

---

