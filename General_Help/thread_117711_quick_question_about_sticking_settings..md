---
title: "quick question about sticking settings."
date: 2006-01-15
forum: General Help
---

### Post by loud_tiger on 2006-01-15
i have to use 855resolution to reset my resolution to 1280x768 every time on my laptop. i have the "Make default for this computer" checkbox checked in the menu under System -> Preferences -> Screen Resolution, but when i reboot the system, i lose my widescreen resolution again. 

also, for my wireless settings, how do i define the key to be "open" in the interfaces file? i basically have to type 

sudo iwconfig ath0 key "xxxxxxxx" open
sudo dhclient ath0

every time i start up the computer. 

if i could get these two fixes "permanent" on my system, that'd be great. everything else works beautifully!

thanks for your help.

---

### Post by loud_tiger on 2006-01-15
ok, solved the resolution issue by putting the line in my bootmisc.sh. can i do the same for the wireless settings?

---

