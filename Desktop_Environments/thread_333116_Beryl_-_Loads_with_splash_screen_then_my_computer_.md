---
title: "Beryl - Loads with splash screen then my computer restarts?"
date: 2007-01-06
forum: Desktop Environments
---

### Post by Kilk on 2007-01-06
Hey everyone I recently just got Beryl all installed from the Wiki guide at beryl project home, and when I go to the terminal and type beryl and hit enter it brings up the splash screen of beryl like it is loading and then it restarts like I hit CTRL+ALT+BACKSPACE when I hadn't and it doesnt do nor change anything..I am using a NVIDIA GeForce2 MX400 64MB graphics card...

---

### Post by aidanr on 2007-01-06
type the following in the terminal and see if it still happens

rm -Rf ~/.beryl
rm -Rf ~/.emerald
beryl-manager

also are you using xgl, aiglx or nvidia drivers?

---

### Post by Kilk on 2007-01-06
> **aidanr said:**
> type the following in the terminal and see if it still happens

rm -Rf ~/.beryl
rm -Rf ~/.emerald
beryl-manager

also are you using xgl, aiglx or nvidia drivers?

I am not sure and I followed this guide [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) and I have a NVIDIA GPU...

---

### Post by orb9220 on 2007-01-07
The command to run beryl is

beryl-manger not beryl

to have beryl run on startup you add it to sessions-manger on startup tab.

---

### Post by Kilk on 2007-01-07
> **orb9220 said:**
> The command to run beryl is

beryl-manger not beryl

to have beryl run on startup you add it to sessions-manger on startup tab.

No offense but that did not help at all you just said what I need help with...Putting it in sessions would just make is constently restart...Also my ubuntu is completely messed up now as I try to get on it and it says some error with X server and stuff and then I cant do anything at all.....And if I run beryl at all it just give splash screen and ubuntu restarts....the manager if I load it, it does nothing at all....besides gives the little icon at the top with options but nothing changes on ubuntu....

---

