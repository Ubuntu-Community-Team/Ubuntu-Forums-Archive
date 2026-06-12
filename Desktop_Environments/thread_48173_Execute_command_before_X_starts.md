---
title: "Execute command before X starts"
date: 2005-07-11
forum: Desktop Environments
---

### Post by PaiTrakt on 2005-07-11
I am using the [855resolution](http://perso.wanadoo.fr/apoirier/) software on my laptop to get my wanted screen resolution. As far as I have understood the readme, I need to execute the command '855resolution 3c 1400 1050' before X starts on boot to get a resolution of 1400 x 1050. How can I execute this command before X? I have googled a bit, and I think I need to create a nifty little bash-script and place it in the folder /etc/init.d/. Is this correct? And how should the bash-script be then?

---

### Post by PaiTrakt on 2005-07-16
Got it!
All I did was to place my command  in one of the files placed in /etc/init.d/
Works like a charm :)

---

