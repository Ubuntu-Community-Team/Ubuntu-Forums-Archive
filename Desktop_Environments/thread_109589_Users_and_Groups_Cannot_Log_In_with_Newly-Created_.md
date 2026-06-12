---
title: "Users and Groups: Cannot Log In with Newly-Created User"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Wolfey on 2005-12-28
I have figured out how to add new users in Ubuntu, but I'm unable to actually log into it with a user that I've just created.  Here are the steps I've followed, once I've logged into Ubuntu (currently as "root"):
[LIST=1]
[*]Clicked on System -> Administration -> Users and Groups
[*]Clicked on "Add User..."
[*]Filled in the fields for Username, User Password, and Confirmation (making sure the last two were exactly the same)
[*]Clicked OK to confirm the addition of this user, which will now be visible in the "Users and Groups" window
[*]Clicked OK to close the "Users and Groups" window
[*]Logged out of Ubuntu
[*]Attempted to log back in with the new account
[*]Got the following error message:

> Incorrect username or password.  Letters must be typed in the correct case.[/LIST]
I have absolutely no idea what I'm doing wrong here - is there a step I forgot to follow somewhere?

Thank you for any help you can provide to fix this problem :)

---

### Post by peanut butter on 2005-12-31
no you dident do anything wrong you might want to try upgrading to breezy. i did exactly what you did in hoary in breezy and it works just fine

---

### Post by Wolfey on 2006-01-02
I just tried upgrading to Breezy (following the instructions provided in the [BreezyUpgrade]("https://wiki.ubuntu.com/BreezyUpgrade") Wiki, upgrading via Synaptic), and after restarting, I don't have a graphical interface anymore :(

I have absolutely **no** idea what went wrong - I followed those instructions, restarted the laptop, and when I try to boot into Ubuntu, it brings up a blue screen that says:

> I cannot start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

<Yes> <No>
But I cannot select either of those, as it immediately brings up two more lines, with white text on a black background:

> Ubuntu 5.10 "Breezy Badger" lc2464 tty2

lc2464 login:
I can still log in with the root username/password, but am left at the command line - I don't know what can be done to restore what was broken as a result of the upgrade :cry:

**[EDIT]**
This isn't directly related to the above, but when I tried to update packages in Ubuntu prior to this upgrade (even if I didn't actually upgrade anything), after restarting the laptop, my boot menu list was completely messed up - none of the selections would work without editing them.

Fortunately I had a Knoppix CD on hand, and after booting up my laptop with it, I found both the original and backup menu.lst files - I copied those to my desktop, printed them out, restarted the laptop without the CD, and changed one of its boot options to look exactly like the one I used to boot into Ubuntu before.  After doing that, and successfully booting into Ubuntu, I replaced the messed-up menu.lst's data with that of the working backup copy's data, and after that, the boot menu problem is fixed...

...Until I do (or try to do) another upgrade followed by restarting the laptop, in which case the boot menu is messed up again, forcing me to repeat the last few steps above to get things working again.

Would setting menu.lst to read-only keep the boot menu from being messed up during these upgrades?
**[/EDIT]**

---

### Post by Wolfey on 2006-01-28
The loss-of-graphical-interface problem has been solved, thanks to what has been tried in the topic "[ Upgraded from 5.04 (via Synaptic): No GUI, But Can Still Log In](http://ubuntuforums.org/showthread.php?t=113951)" :)

Unfortunately, I *still* cannot log in with the user accounts I've created...And after updating via Synaptic again, I can't log in as root, either! :(

(**NOTE:** This is only when trying to log in via GNOME - By the command line, I can log in as root, but I still can't log in with any other user accounts.)

---

### Post by Wolfey on 2006-02-02
*(Bumping topic...)*

Since I'm no longer using Ubuntu 5.04 after the upgrade to Ubuntu 5.10, could I get this topic moved to either the "Installation and Upgrade Help" or "Ubuntu 5.10 Support (GNOME)" forum?  Thanks in advance :)

---

### Post by Iandefor on 2006-02-05
Try using the command adduser in a terminal. ```
man adduser
``` for more information. To use it, open up a terminal and type in```
sudo adduser
```

---

### Post by Wolfey on 2006-02-07
Thank you! Now I can create new user accounts and actually be able to log into them this time! =D>

I also tried running "Users and Groups" again, but any user created with it cannot log in...Yet if that same user is created with "adduser", it works.  I wonder why it works in one, but not the other? :-k

---

### Post by Wolfey on 2006-06-18
Recently updating a few things via Synaptic (though I'm not sure which ones were responsible for this) seems to have fixed the issue that I mentioned in my first post: Users created with "Users and Groups" can log in now! =D>

---

