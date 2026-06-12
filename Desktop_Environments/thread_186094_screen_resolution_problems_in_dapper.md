---
title: "screen resolution problems in dapper"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Swab on 2006-06-01
I just did a clean install of dapper, and now the only option I have for resolution is 800x600 , tried changing my xorg.conf to 1024x768 , but makes no difference. 

Any ideas?

---

### Post by eqisow on 2006-06-01
Boot into the command line (recovery mode) and run *sudo dpkg-reconfigure xserver-xorg*. Leave everything at default (ie. just hit enter) until you get to the part where it ask about maximum resolution and refresh rate. There will be options for Simple, Medium, and Advanced. Choose 'Medium' if you know your monitors max refresh/resolution. If you do not know, choose 'Simple' and select your screen size. Finish the process and reboot.

Note: To choose an option press 'Spacebar', to confirm your choice press 'Enter'.

---

### Post by Swab on 2006-06-01
Thanks, it's all good now ;)

---

