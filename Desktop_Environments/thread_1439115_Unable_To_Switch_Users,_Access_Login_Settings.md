---
title: "Unable To Switch Users, Access Login Settings"
date: 2010-03-25
forum: Desktop Environments
---

### Post by wroseland on 2010-03-25
I have several things that are not working.  The first is that I can no longer switch users.  I used to be able to click my user name on the task bar and switch to another user.  I believe that I could click my full user name and it would let me switch (maybe the process was a liitle different). Now I have selections for Status, Log out, Suspend, Hibernate, Restart, and Shut Down.  My full user name is at the top of the menu and appears to be in "disabled" text.  I tried to use the "login screen settings" menu selection but everything is disabled and when I select "unlock", nothing  happens.  I ran sudo gdmsetup and this message was displayed when I selected "unlock".

** (gdmsetup:2595): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files

Is this a problem?  How do I switch users?

Thanks,
Winton

---

### Post by quixote on 2010-03-27
They put the switch user items in a different place from the shutdown-related items.  (Don't ask me why.)  If things were working normally, you could right-click on an empty space in the panel, select "Add to Panel", and then select "user switcher" in the window that pops up.  It should add that back to the panel for you.

However, it sounds like you have something worse than a missing applet going on.  Judging by some other threads with that same error message, that's some kind of bug, but I'm not sure their fixes will work for you because it sounds like the manifestation is a bit different.  Your problem isn't auto-login or choosing between different display managers.  Still, maybe there'll be something useful here...

[http://wwww.ubuntuforums.org/showthread.php?t=1308700](http://wwww.ubuntuforums.org/showthread.php?t=1308700), and the link mentioned in #18 in that thread: [http://lani78.wordpress.com/2009/07/30/gnome-auto-login-in-ubuntu-9-10-karmic-koala-alpha-3/](http://lani78.wordpress.com/2009/07/30/gnome-auto-login-in-ubuntu-9-10-karmic-koala-alpha-3/)

---

### Post by wroseland on 2010-03-28
Thanks that information did help.  I tried KDE 4 so my manager was no longer gdm.

---

