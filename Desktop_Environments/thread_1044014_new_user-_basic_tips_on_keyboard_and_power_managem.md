---
title: "new user- basic tips on keyboard and power management setup"
date: 2009-01-19
forum: Desktop Environments
---

### Post by AM_SOS on 2009-01-19
hello all!

i am a beginner with Ubuntu 8.10 and initial impressions promise a satisfying experience vis-a-vis my Win XP / Vista.
let me start by thanking the Ubuntu community for propagating the idea of open source software. moreover, help from the online community means one is no longer bound to microsoft.
i have a simple query to start with. since i have shifted from Win XP now, i have not been able to properly configure the keyboard. e.g. 
- the right Alt key doesn't work in Open Office 3. when i want to go the the menus while typing, i can do so only with the left Alt key. and this too causes the menu to drop down with just one press. so there seems to be no way in which i can use the Alt+T shortcut to quickly reach the Options menu.
- similarly, when i press the Back button in Firefox this does not cause the page to revert back to the previous page. i have use the pointer to press the back button on the Firefox toolbars.
- finally, in the event of low battery Gnome power management gives out a warning sign. however, there doesn't seem to be any way in which activate an audio warning for the same!
any tips friends ?
thanks!

---

### Post by adamlau on 2009-01-19
You can reset your keyboard layout with the following:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by AM_SOS on 2009-01-19
i can reset it to what ? cos i have just begun using it anew! so am not sure how this is going to help. btw, i had come across similar problems in XP when sometimes the left Alt key would not work in MS Office. but this was solved by selecting the keyboard layout as US international or something like that. so should i still go ahead and run the command you suggest?
thanks!

---

### Post by adamlau on 2009-01-19
Yes, choose your keyboard layout when prompted to do so.

---

### Post by AM_SOS on 2009-01-22
hi,
i tried running this command but got a lil mixed up as to the values i was supposed to input. is there any link (great if its illustrated) which shows how i can do this?
thing is i don't want to take a risk by entering something wrong and causing further complications for myself.
actually, i want to just sort out these things and make them life my XP settings-
-i can shortcut to the menu in OO Writer only with the Left Alt key and not the Right one. in fact, the right Alt key seems pretty much dead in keyboard navigation and clearly this is because of the configuration.
-while typing in OO Writer when i press the BackSpace command to delete a word it also ends up deleting the blank space after the previous word. i therefore have to press the space bar and then only enter the corrected word. this again was not the case in MS Word and this helps in saving time.
-i have no idea how to configure my Win logo key. how is one to set it open the Gnome main menu icon?
thanks

---

