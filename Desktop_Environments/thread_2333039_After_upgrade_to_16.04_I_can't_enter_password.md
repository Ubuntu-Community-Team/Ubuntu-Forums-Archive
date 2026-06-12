---
title: "After upgrade to 16.04 I can't enter password"
date: 2016-08-06
forum: Desktop Environments
---

### Post by danielsender on 2016-08-06
I have a 32b vintage HP laptop - I upgraded from 14.04 to 16.04 and the process finished successfully. However now the system's GUIs (e.g. software update, etc.) appear with the box for the password grayed out. On the other hand there is not problem in entering the password from the command line, e.g. "sudo xxx".

I appreciate any pointers.

Daniel

---

### Post by danielsender on 2016-08-08
Should I perhaps go to a different forum?

---

### Post by howefield on 2016-08-09
Is the GUI password issue restricted to "software installation" applications ? 

Eg, if you have gparted installed, can you load and successfully enter the password (or some other application that requires the password, eg Passwords and Keys, right click on Gnome 2 Key Storage, select unlock and it will ask for a password, remember to right click and lock before exiting) ?

---

### Post by danielsender on 2016-08-09
gparted does the same thing, the password boxes are grayed out. I called "seahorse", unlocked the keyring and I entered the password and I locked it again. I also tried additional drivers and is the same result.

---

### Post by danielsender on 2016-08-12
I actually posted this on the "Installation and Upgrades" forum, but I got no help, so perhaps a good soul on this forum can give me a clue. I have a vintage HP laptop (32b) that was running 14.04.5 OK. I upgraded to 16.04.1 and the installation finished OK, however all GUIs on the system show the password box grayed out when I have to elevate to administrator priviledges. However if I open a terminal I have no problem sudo'ing, e.g. sudo xxxx.... This happens on GUIs like software update, gparted, etc.

[edit] I just noticed something: there are two users on the system, both with administrator priviledges. If in the username I changed in these GUIs the username, its password box is not grayed out and if I revert back to my username then the box is not longer grayed out. What's going on?

[edit2] I just repeated the same procedure of updating to 16.04 from 14.04 on a Dell Desktop (32b) and the situation is exactly the same, that is I have to rock back and forth on the username in order to make the box enabled.

Thanks in advance.

---

### Post by howefield on 2016-08-12
Duplicate threads merged.

---

### Post by danielsender on 2016-08-12
OK - It appears that is a bug since nobody has any ideas.

---

