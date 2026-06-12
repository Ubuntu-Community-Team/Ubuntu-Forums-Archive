---
title: "Messed it all up"
date: 2005-09-09
forum: Desktop Environments
---

### Post by Anonymous Guy on 2005-09-09
Being the weird guy I am, I set my user's home directory to something WRONG and now I can't login [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG] 

Is there any way I can fix this?  ;-)

---

### Post by codejunkie on 2005-09-09
[QUOTE=Anonymous Guy]Being the weird guy I am, I set my user's home directory to something WRONG and now I can't login [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG] 

Is there any way I can fix this?  ;-)[/QUOTE]
choose recovery mode at the grub menu then enable the root account with this ```
passwd root
``` set a new password for the root user reboot your computer with ```
init 6
``` when you get to the ubuntu login screen press 
ctrl+alt+F1 this will take you to a virtuial console here login as root and enter the password you just setup now type ```
killall gdm
``` and then ```
startx
``` this will let you login to a gui as the root user where you can create a new user account and copy your files over from your home directory or repair your user account hope this helps.

---

### Post by Anonymous Guy on 2005-09-09
Ok that worked thanks  :smile:

---

