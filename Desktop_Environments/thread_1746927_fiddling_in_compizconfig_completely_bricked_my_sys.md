---
title: "fiddling in compizconfig completely bricked my system"
date: 2011-05-02
forum: Desktop Environments
---

### Post by wim.glenn on 2011-05-02
hello , last night i upgraded to 11.04 but now i'm wishing i hadn't.  the upgrade seemed to work ok, but i ended up with an unfamiliar interface which i've now learned is called unity.  i was trying to get my desktop cube/rotate cube back in compiz settings manager, and i can't really explain how i did it but I soon broke the GUI completely.  when i tried to enable the cube something popped up in the top left corner, one of those dialogs to resolve conflicts i think, but i could not read what the message was because the stupid unity panel and top menu bar were painting over the top of it.  the top part of the dialog was obscured so i couldn't drag the dialog into view and i couldn't recall the keyboard modifier (is there one?) to allow move the dialog to a readable part of the screen by grabbing it from anywhere.  not a great triumph of UI design there.  so i just clicked one of the buttons to make the dialog go away and give my focus back , but after that i couldn't move any windows or do anything.  i guess i disabled an essential part of unity.  after a reboot, i just get the blank desktop.  no opening up a terminal with ctrl+alt+t, no right click menu, no panels, icons, launchers, nothing...!  the only things i seem to be able to do is move the cursor around on the screen (wheee!), go ctrl+alt+F1/F7 back and forth to a terminal and the bricked GUI, and ctrl+alt+del to reboot.  i tried unity --reset at the terminal, which prints out some crap then segfaults.  i tried reseting compiz settings to defaults, no dice.  the only way i'm able to post here is to boot up in safe mode.  can someone suggest some things to try to repair stuff?

---

### Post by burpootus on 2011-05-02
> **wim.glenn said:**
> hello , last night i upgraded to 11.04 but now i'm wishing i hadn't.  the upgrade seemed to work ok, but i ended up with an unfamiliar interface which i've now learned is called unity.  i was trying to get my desktop cube/rotate cube back in compiz settings manager, and i can't really explain how i did it but I soon broke the GUI completely.  when i tried to enable the cube something popped up in the top left corner, one of those dialogs to resolve conflicts i think, but i could not read what the message was because the stupid unity panel and top menu bar were painting over the top of it.  the top part of the dialog was obscured so i couldn't drag the dialog into view and i couldn't recall the keyboard modifier (is there one?) to allow move the dialog to a readable part of the screen by grabbing it from anywhere.  not a great triumph of UI design there.  so i just clicked one of the buttons to make the dialog go away and give my focus back , but after that i couldn't move any windows or do anything.  i guess i disabled an essential part of unity.  after a reboot, i just get the blank desktop.  no opening up a terminal with ctrl+alt+t, no right click menu, no panels, icons, launchers, nothing...!  the only things i seem to be able to do is move the cursor around on the screen (wheee!), go ctrl+alt+F1/F7 back and forth to a terminal and the bricked GUI, and ctrl+alt+del to reboot.  i tried unity --reset at the terminal, which prints out some crap then segfaults.  i tried reseting compiz settings to defaults, no dice.  the only way i'm able to post here is to boot up in safe mode.  can someone suggest some things to try to repair stuff?

Login to classic, go to compiz and enable the unity plugin which will disable the cube. The cube and unity have a conflict.

---

### Post by wim.glenn on 2011-05-02
thanks, i was able to restore it now.  i did however have to re-enable the login menu , as the machine has only one account and i it was set to log in automatically.

---

