---
title: "Can't change main menu"
date: 2008-10-07
forum: Desktop Environments
---

### Post by mlgdr on 2008-10-07
I tried to configure my main menu. When I select System/Preferences/Main Menu I get the menu editor as described in many threads. But when I select e.g. a new application to appear in the "Applications menu" the check mark disappears after a few seconds again. Same when I deselect an existing entry. After a few seconds the check mark is automatically set again.
Seems that there is a background process automatically reverting my settings after a few seconds again.

What's wrong here?


Regards

  Martin

---

### Post by majorhabib on 2008-10-09
What Ubuntu version do you use?
Did you do anything recently like upgrading from older distribution?

---

### Post by mlgdr on 2008-10-09
I use 8.04. I upgraded to 8.04 when it came out, so quite some time ago.

---

### Post by cwsnyder on 2008-10-09
The only way I was able to reproduce your problem was to make a folder entry.  If the folder was empty, I could not select the folder and make it show up.  Again, if the folder has an entry which is checked, I could not de-select the folder.

Is this your problem?

---

### Post by Bootsy Collins on 2008-12-17
I'm having the same problem with a fresh install (as in within the last two hours) of 8.10/Intrepid.  This is not an upgrade, but a complete wipe/format/install.

What I do:
click on System --> Preferences --> Main Menu

What I see at first:
in the left hand panel, Applications is currently highlighted, with possible submenus below.  In the center panel, the possible submenus are listed again, with some of them checked.  The ones checked are the ones that actually show up when I open the Applications menu from the menubar.
Currently, Accessories, Games, Graphics, Internet, Office, Sound & Video, and Universal Access are checked, followed by a separator, followed by Add/Remove.

What I do:
check "Programming," which is not currently checked.

What happens:
three seconds later, the check vanishes.

---

### Post by Bootsy Collins on 2008-12-17
> **Bootsy Collins said:**
> I'm having the same problem with a fresh install (as in within the last two hours) of 8.10/Intrepid.  This is not an upgrade, but a complete wipe/format/install.



UPDATE:  problem solved, and it should have been obvious.  I couldn't enable those submenus because there weren't any applications installed yet that belonged in those submenus.

---

