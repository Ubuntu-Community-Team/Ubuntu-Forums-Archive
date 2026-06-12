---
title: "[SOLVED] Programs close upon opening"
date: 2008-12-19
forum: General Help
---

### Post by melenor on 2008-12-19
all i was doing was changeing my theme, when the appearence editor closed. when i tired to re open it, it would just flash open then close. so i restarted thinking that, restarting might solve it. It did not, now almost all of my apps will only open for a blink second then close. Thanks for any help.


EDIT: running anything from the command line gives the error "Segmentation Fault"

---

### Post by pytheas22 on 2008-12-19
> running anything from the command line gives the error "Segmentation Fault"

Every single application segfaults?  Are you able to keep the terminal window itself open?  Could you please post the entire command-line output of an application that crashes?

Also, try creating a new user account.  You can do this using the graphical interface at System>Administration>Users and Groups if it works.  If that utility also crashes, you can create a new user by typing a command like:
```

sudo adduser testuser
```

This will create a new user named 'testuser'.  Try logging into a Gnome session as that user.  Do things work there?  If so, it should be easy to resolve the problems with your main user account.

---

### Post by levif on 2008-12-19
I personally do not have this issue, but a friend of mine cannot keep anything open at all, not even a terminal.

---

### Post by melenor on 2008-12-20
I fixed it, it was caused by a theme that i was creating i am actually not quite sure what happened, but i was able to fix it, by cd' ing to the theme directory and rename the gtkrc file and restart X. thank you for all your help.

---

### Post by pytheas22 on 2008-12-20
> I personally do not have this issue, but a friend of mine cannot keep anything open at all, not even a terminal.

Does your friend still have the same problem if he creates a new user account?  Since he can't keep a Gnome terminal open, he can get to a virtual terminal by pressing control-alt-F2 and use the 'adduser' script to create a new account, as outlined in my post above (press control-alt-F7 to get back to Gnome).

---

### Post by levif on 2008-12-23
Apparently it works sometimes (under the new user) but after a few hours of use, nothing will open anymore, yielding a segfault.

---

### Post by pytheas22 on 2008-12-23
> Apparently it works sometimes (under the new user) but after a few hours of use, nothing will open anymore, yielding a segfault.

That's really weird.  I'm thinking it might come down to some major problem with Gnome.  Does he have better luck under a different desktop environment?  He could install KDE for example by typing:
```

sudo apt-get install kubuntu-desktop
```

then choose to log into KDE instead of Gnome at the login screen.  If things are stable in KDE, then reinstalling the ubuntu-desktop package may solve the problem.

Also, has he checked the system logs to see if they give any clue?  If things are segfaulting, something really strange is going on.

---

