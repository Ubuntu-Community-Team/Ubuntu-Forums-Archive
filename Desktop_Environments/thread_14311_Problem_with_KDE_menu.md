---
title: "Problem with KDE menu"
date: 2005-02-06
forum: Desktop Environments
---

### Post by SickBoy on 2005-02-06
After a language change (from English to Spanish) K menu seems to be non writeable. I mean, I go to the menu editor, do some changes and they doesn't appear. Also the menu is still in english and applications I install or uninstall don't change in the menu.

I tried deleting whole $HOME/.kde dir but that didn't helped. Also dpkg-reconfigure kicker didn't helpped.

Thanks in advance.

P.S. : I'm using warty

---

### Post by Ironi on 2005-02-06
[QUOTE=SickBoy]After a language change (from English to Spanish) K menu seems to be non writeable. I mean, I go to the menu editor, do some changes and they doesn't appear. Also the menu is still in english and applications I install or uninstall don't change in the menu.

I tried deleting whole $HOME/.kde dir but that didn't helped. Also dpkg-reconfigure kicker didn't helpped.

Thanks in advance.

P.S. : I'm using warty[/QUOTE]
 Try removing **~/.local/share/mime/** ... if that doesn't work, you could remove the entirety of **~/.local** as well. That should hopefully fix the problem, unless there's a bug somewhere.

---

### Post by SickBoy on 2005-02-06
[QUOTE=Ironi]Try removing **~/.local/share/mime/** ... if that doesn't work, you could remove the entirety of **~/.local** as well. That should hopefully fix the problem, unless there's a bug somewhere.[/QUOTE]
 Unluckly that does not solve the problem. Does somebody know where is the config file for the K menu stored?

---

### Post by Ironi on 2005-02-06
Okay, I just installed kde-i18n-es and switched my language to Spanish. Everything seems to be fine, and menu changes stick. However, I'm using the version of KDE currently in hoary (4:3.3.2-1ubuntu6).
   
 I would guess that internationalization might be broken with warty's KDE. Besides recommending a dist-upgrade to hoary, I don't know how you would resolve your problem. [Try Google, perhaps.]("http://www.google.com/search?q=kde+i18n+warty")

---

### Post by SickBoy on 2005-02-07
[QUOTE=Ironi]Okay, I just installed kde-i18n-es and switched my language to Spanish. Everything seems to be fine, and menu changes stick. However, I'm using the version of KDE currently in hoary (4:3.3.2-1ubuntu6).
   
 I would guess that internationalization might be broken with warty's KDE. Besides recommending a dist-upgrade to hoary, I don't know how you would resolve your problem. [Try Google, perhaps.]("http://www.google.com/search?q=kde+i18n+warty")[/QUOTE]
 I tried switching to USA english and everithing goes back to english but still no luck changing the menu. 

Tried deleting ./config also but no luck. 

Maybe I update to hoary

---

### Post by SickBoy on 2005-02-09
[QUOTE=SickBoy]I tried switching to USA english and everithing goes back to english but still no luck changing the menu. 

Tried deleting ./config also but no luck. 

Maybe I update to hoary[/QUOTE]
 Yahoooo!!! 

Found solution. Just delete /var/tmp/kdecache-$USER folder and everything started again right.

---

### Post by quini on 2005-06-26
[QUOTE=SickBoy]Yahoooo!!! 

Found solution. Just delete /var/tmp/kdecache-$USER folder and everything started again right.[/QUOTE]

Doesn't work for me.  I've set kde to first use catalan, second spanish language, and added apps (using apt-get) are not added to menu.

I've also deleted ~/.local/* also with no luck...

I've installed 3 games to try: lbreakout2, pingus and frozen-bubble... only the last one has been added to the games menu   :? 

Any other idea?   :roll:

TIA

---

