---
title: "[SOLVED] I am not given an Option To Shutdown and Restart"
date: 2008-07-21
forum: Desktop Environments
---

### Post by charlescarroll1 on 2008-07-21
I am running Ubuntu 8.04, on my Inspiron 1501 laptop.  Ever since I installed Ubuntu 8.04, I haven't been able to shutdown or restart through Ubuntu.  When I go to "Quit", the only options I get are Log Out, Lock Screen, Switch User, Suspend and Hibernate.  

Does anyone else have the same issue or know how to fix it?

---

### Post by Gizkaguy on 2008-07-21
Does the account your using have administrative access?

---

### Post by charlescarroll1 on 2008-07-21
When I go to User Settings, and User Privileges, "Administer the system" is checked.  Is this the same as administrative access?

---

### Post by armageddon08 on 2008-07-21
hey we are aboard the same ship bud.....i too don't have the two options. my problem however arised after I installed OpenGEU metapackage. If you get any solution please share.

---

### Post by NilsE on 2008-07-21
Go into Login window preferences and make sure Show actions is selected.

---

### Post by rogier.de.groot on 2008-07-21
Can you open a terminal window and shutdown or restart with the commands "sudo halt -p" and "sudo reboot" ?

---

### Post by armageddon08 on 2008-07-21
Yup......it is possible to shutdown or reboot from the terminal. i am also able to do those actions from the login window. But I don't see any option in Quit menu.

---

### Post by rogier.de.groot on 2008-07-21
Hmmm... I have a hunch there must be some kind of setting for this somewhere in the gnome configuration, but I can't find it using gconf-editor. Maybe that's because I'm running Linux Mint instead of regular Ubuntu though...

---

### Post by NilsE on 2008-07-21
> **rogier.de.groot said:**
> Hmmm... I have a hunch there must be some kind of setting for this somewhere in the gnome configuration, but I can't find it using gconf-editor. Maybe that's because I'm running Linux Mint instead of regular Ubuntu though...
I posted where to fix it above.

This of course is assuming you mean the the shutdown and restart icons on the popup that shows when you click on the quit icon.

---

### Post by armageddon08 on 2008-07-21
Yes, I checked it......Show actions is selected. but can't get it fixed.

---

### Post by NilsE on 2008-07-21
OK.  One other possibility is that you may not have permissions to retart and shutdown so look in Authorization GUI to see if you do.

---

### Post by charlescarroll1 on 2008-07-21
> **NilsE said:**
> Go into Login window preferences and make sure Show actions is selected.

This worked for me!  I most likely deselected it while I was setting up the Log in options when I first installed Ubuntu.  Thanks NilsE.

---

### Post by armageddon08 on 2008-07-22
> **NilsE said:**
> OK.  One other possibility is that you may not have permissions to retart and shutdown so look in Authorization GUI to see if you do.

Even this did not work. Can you please elaborate what steps to follow?
BTW, I am using KDM as my login manager. IS that the reason?

---

### Post by neotorture on 2008-08-17
I am a new user of Ubuntu but really happy with it. So apologize if I made a wrong comment.

I face the similar problem. I'm running on Ubuntu 8.04 but also has KDE Desktop installed (just want to try).

When I want to shutdown I have to logout from GDM and shutdown from KDM screen. But shutdown is normal when I'm running on KDE.

My understanding is that even tough I'm running on Gnome the GDM is not running. It might be related to the KDM/GDM default option during KDE installation.

Unless the Kubuntu Desktop is unistalled then the shutdown button will not be visible. Because GDM is not running and you have to go to KDM to shutdown.

As I said, I might be wrong because I'm still trying to find away to solve it.

---

