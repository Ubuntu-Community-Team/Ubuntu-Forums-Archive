---
title: "How to reset desktop to default when no gui available?"
date: 2009-10-06
forum: Desktop Environments
---

### Post by WhiteHorse007 on 2009-10-06
From the default destktop of ubuntu 9.04 (the one having a vertical menu at the left for the applications by categories, and a vertical menu at the right for kind of a file navigation, the center area displaying the available application of the selected category), I switched my preference to the other desktop showing  a horizontal menu bar at the top, with the applications running in the center area, and a horizontal button bar of opened applications at the bottom. So I had the new desktop working for a while yesterday night. But when I started up my Acer One 110L this morning the only things I had on the desktop screen were a few icons, but the top horizontal menu had disappeared, along with the bottom horizontal button bar.

I am totally illiterate to ubuntu, I find it very difficult to try to find things throughout the maze of forum pages and other documentations available for ubuntu.

Is there a way of resetting things so that they work as the default desktop environment? An easy way I mean.

Right now I have no user interface to graphically help me to do this.

No menu available to reset preferences. EXCEPT that when I right-click on the desktop I get this menu: 
  Create Folder
  Create Launcher...
  Create Document
  Clean Up by Name
  Keep Aligned
  Change Desktop Background

If I click on the Create Launcher... item I get a dialog window like
[Application]
[           ]
[        ] [Browse...]
[                     ]
Cancel and Ok button

Could someone help me please?

Thanks.

---

### Post by earthpigg on 2009-10-06
make a launcher with 'gnome-terminal' as the command.

use that bad boy to open a terminal.

in the terminal, type 'nautilus' and press enter, which should open the graphical file manager.

view -> show hidden files.

in your home directory, find .gconf. 

inside .gconf, find the 'panel' folder and delete it.

close nautilus.

at that terminal, type 'sudo killall Xorg'

log back in.


if that does NOT fix it, repeat the above but delete the entire .gconf folder.

---

### Post by WhiteHorse007 on 2009-10-07
Thanks for taking the time to help. Unfortunately I was too anxious to get back to work. So after an hour of research I decided to make a backup of my personal files and then reinstalled ubuntu.

I appreciate your help though and will document your help tips so that if this ever happens again to me I will use your instructions.

Thanks again!

---

### Post by Ubuspaz on 2009-11-30
Worked for me. Thanks.

---

