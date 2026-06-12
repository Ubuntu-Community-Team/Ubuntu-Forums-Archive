---
title: "Strange problem with keyboard layout settings"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Luuraja on 2005-12-17
Hi.
Installed 5.10 without visible errors but after that I can\t use my estonian keyboard. Language packs are installed, language settings seem perfect  and keyboard settings show me what everything is OK - estonian selected and made default.
But keyboard works as US English...

Tried to use swedish keyboard layout, its very similar, but without any success. US English stills.

---

### Post by kairu0 on 2005-12-17
Are you using Gnome or KDE?

---

### Post by Luuraja on 2005-12-17
Woah! Everything is OK now!
õüäö - these are characters I needed. And ,.()&%¤#"'>< are in right place.

Can't find the proper source now, but command 
```
sudo dpkg-reconfigure xserver-xorg
```
 in terminal helped me out. It brings up interface for configuring xorg - you must be patient and read everything before execution.
Estonian keyboard abbreviation is "ee" and when it asked about dead keys elimination I answered "nodeadkeys". 
Now Gnome ->Preferences->Keyboard->Layout shows that I have "generic105-key (intl) PC" keyboard with "Estonia eliminate dead keys" layout.
BTW my keyboard is Logitech Y-ST39

I think this kind of trouble is a very serious bug and must be solved in Dapper Drake.

---

### Post by kairu0 on 2005-12-17
I specified my keyboard as "Japanese" in the Ubuntu install and it got configured in X11 as a PC105. Go figure! I had to modify the file by hand to be JP106.

---

### Post by Luuraja on 2005-12-17
When I installed Ubuntu I am sure I did everything right.  
Install process asked me for my language then selected automatically keyboard layout.
It asked me to download of additional language files, which was successful.
First bootup was in purely in Estonian, but after logging in I was shattered - Gnome in Estonian but keyboard...

By the way. Ubuntu stills my favorite Linux - light, clear, scalable and with perfect mood.

---

