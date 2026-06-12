---
title: "mess - deleted one user main folder"
date: 2011-04-14
forum: Desktop Environments
---

### Post by mosaic2s on 2011-04-14
i have system that was cloned from another system hence the user was same in both computer.
i changed the computer name - to TANU. then i added another user - BANU. i gave admin rights to second user.
logged out the first user DON- who is now only the desktop user.
before deleting the account through users and groups - i deleted the folder DON  from home folder.

crisis. i restarted the comp. unable to login. i had created automatic login for both users.
question: how to restore the folder DON while using root shell. i am still novice.

---

### Post by false truths on 2011-04-14
In your GRUB menu, load Ubuntu's recovery mode. That will load you into single-user-mode, which is essentially a root login to the Ubuntu gui.

If your GRUB menu doesn't appear on startup, hold the shift key to make it appear.


Once you're logged in as root, simply copy the other user's user folder and rename it to match the missing user's name. Then remove any items from that folder's contents that you want to keep in the administrator's contents.

I've had to do this a few times because I accidentally broke my user accounts in very similar ways.

---

### Post by mosaic2s on 2011-04-15
did more trial and error. and finally worked it out like this.

i logged out by ctrl-alt-del.
logged in the other user.
went to login screen in the Administration and made BANU as the default login.

then created the folders for previous DON user using sudo nautilus in terminal. then deleted the user from USERS AND GROUPS.

working fine now.

---

