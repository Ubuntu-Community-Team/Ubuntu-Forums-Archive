---
title: "Not loading GNOME or XFCE"
date: 2008-12-25
forum: Desktop Environments
---

### Post by fat_man_dan on 2008-12-25
After booting up my machine I get the login screen, I type in my username and password and start logging in. My screen changes to my background colour and I still have my mouse, but non of the toolbars or any other application loads. I have attempted logging into my GNOME, XFCE, Failsafe GNOME sessions and non of them seem to work.

Any help or suggestions would be appricated

---

### Post by pytheas22 on 2008-12-25
Did this always happen since you first installed Ubuntu, or is a recent problem?

If it's a new problem, try this:

1. at the login screen, press control-alt-F2
2. you'll be brought to a command-line.  Login there and run this command:
```

sudo adduser testuser
```

Follow the instructions on the screen for creating a new user.

3. press control-alt-F7 to get back to the login screen.  Login with username 'testuser' and the password that you just set.  Can you login now?

---

### Post by fat_man_dan on 2008-12-25
Creating a new account seems to allow me to log in again correctly

How do I now go about getting the old user accounts to be able to log in?

---

### Post by pytheas22 on 2008-12-25
Try renaming the .gnome and .gnome2 directories in the /home folder of the original user.  In other words, press control-alt-F2 and log in as your original user, then run these commands:
```

mv ~/.gnome ~/.gnome-OLD
mv ~/.gnome2 ~/.gnome2-OLD
```

Then try logging into Gnome as the original user.  If this doesn't work, we may have to experiment with other folders to move.

Also, note that the above solution will cause you to lose any desktop customizations and revert to the default Ubuntu theme.  But it's the easiest way to solve the problem.

---

