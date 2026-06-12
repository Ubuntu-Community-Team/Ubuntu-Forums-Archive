---
title: "Insert key launches Konqueror, not cool."
date: 2009-04-14
forum: Desktop Environments
---

### Post by CodeNosher on 2009-04-14
Hello,

I've upgraded from 7.10->8.04->8.10.  Now when I push the insert key Konqueror launches.  I run gnome, but have Konqueror to address other issues.

Also, when I hit my mute button Pidgin launches!!  I have the mute button configured in my gconf to work as a mute button, yet Pidgin launches anyway.

I have the MS Natural Keyboard Pro/USB/MS Internet Keyboard Pro selected as my Keyboard model.

I've looked in my keyboard shortcuts and can't find anything that would do this.  I've looked in the gconf and can't find anything related there either.

I've got compiz running, but I don't see anything that could be related there either. 

Any ideas where I can look to find out what's telling these to launch?

Now the menu key is acting like a ctrl-z key!!  xev says it's (keysym 0xff67, Menu key) then (keysym 0xffe3, Control_L), (keysym 0x7a, z).

---

### Post by CodeNosher on 2009-04-20
Anyone have any thoughts?  It stopped for a day or two then started up again.

---

### Post by ambdeep on 2009-04-20
have u checked System->Preferences->Keyboard Shortcuts?

---

### Post by CodeNosher on 2009-04-20
Yes.

---

### Post by gali98 on 2009-04-20
Try running
sudo service hotkey-setup start
and see if  the problem still exists.
If it fixes the problem, run
sudo update-rc.d hotkey-setup start 99 1 2 3 4 5 6 .
(make sure you get that period at the end.)
Kory

---

