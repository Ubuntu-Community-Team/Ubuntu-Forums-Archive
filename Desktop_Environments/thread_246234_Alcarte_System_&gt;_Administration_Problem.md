---
title: "Alcarte System &gt; Administration Problem"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Ziggy72 on 2006-08-29
I have 23 items in my System > Administration Alcarte Menu Editor and all of them are ticked.

When I logon as a user all of the items show in the System > Administration drop down list.

However, when I logon as root, only 13 items show in the System > Administration drop down list even though all 23 are ticked in the Alcarte Menu Editor. 

The 13 programs shown appear to be those that are ticked by default at installation - because if I do a "revert", the items shown in the drop down list don't change.

I've tried reinstalling Alcarte, but there's no change.

Can I somehow rebuild the drop down menus for root from the command line?

Actually, where is Alcarte anyway. Typing "alcarte" at the command line gives "command not found", and typing "whereis alcarte" gives "alcarte:".

---

### Post by croak77 on 2006-08-29
That's cause your menu is saved in your user's /home folder. When you logged in as root it looks for the settings in /root. You'll have to edit the menu for each user, so log on as root and run alacarte as root. Maybe that will work never tried it though. You really shouldn't be logging in as root anyways.

---

### Post by Ziggy72 on 2006-08-29
Where is the menu saved in /home?

---

### Post by croak77 on 2006-08-29
It's in one of the hidden folders like .gnome or .gnome2. I'm not using GNOME now so I can't check.

But like I said, you really shouldn't be logging on to gnome as root. If you need to be root use sudo or gksudo.

---

