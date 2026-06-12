---
title: "Cannot change from Metacity to Beryl"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by chumchum on 2007-12-22
Hello all.
I am using ubuntu feisty with dual boot with Windows XP using wubi.
I have Beryl version 0.3.0+git20070323~3v1ubuntu2
?When I first insalled I had the white cube of death , I fixed those, I then had the "Checking for XComposite extension : failed" error which I fixed by editing xorg.conf and now I have another when I try to use beryl through the icon and changing to beryl, the screen flickers and comes back to metacity, when I type "beryl --replace" into the terminal all freezes and I get an error message saying "Checking for non power of two texture support : failed" I have to sign out because of the freezing, I tried searching for a fix, but other cases seem specific to certain grphic cards, so won't work with me. My GFX card is a ATI radeon sapphire X1650 pro (AGP version) and I'm using official ATI drivers, installed with Envy.
Any help will be appreciated

PS: Here is the full error message
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by Bagno on 2007-12-22
Huh? Have you graphics from ATI? If yes, just uninstall X.Org ATI Binary Driver.

---

