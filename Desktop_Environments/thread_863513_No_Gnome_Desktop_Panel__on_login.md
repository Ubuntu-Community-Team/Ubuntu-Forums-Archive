---
title: "No Gnome Desktop Panel  on login"
date: 2008-07-18
forum: Desktop Environments
---

### Post by mys_shekar on 2008-07-18
Hi,
   My desktop was working fine.. And now when I login I am not able to see my Gnome Panel or the terminal...
   I tried logging using fail safe mode... Everything is working fine only in fail safe mode..
   Can anybody help me with this..
 

Regards,
Shekar

---

### Post by Potatoj316 on 2008-07-18
I dont know if this will work, but I can't think of anything else. Press ctrl+alt+F1 and then log in with your username and password. Then type "gnome-panel".  Now press ctrl+alt+F6 (it might be F7 or F5 but Just keep trying the F buttons until one brings you back to your desktop)  If the panel is there it worked, other wise it did not.  Perhaps to have a terminal accessed more easily you could put the terminal on a hotkey (System -> Prefrences -> keyboard shortcuts)

This probably wont make the panel come back after you reboot, but at leas you have it for now.  Maybe when the panel is running it will be easier to actually fix the problem because you have access to your menus.

---

### Post by mys_shekar on 2008-07-18
thanks for the reply...
   tried doing what u suggested but got the error telling "cannot open display"

    Can I reinstall my genome??  Will reinstall effect any of my other applications apart from desktop??

---

### Post by Bethra 0_0 on 2008-07-20
I had the same problem but this advice in another thread solved it for me :-
Quote:
Originally Posted by Nem1976 View Post

"gconftool-2 --recursive-unset /apps/panel" minus the " "

Then reboot & on the login screen under options choose "last login".
I have no idea if the last bit made any difference, but I've got my panel back :)

---

