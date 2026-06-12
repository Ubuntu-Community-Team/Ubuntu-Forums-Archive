---
title: "deleting user and adding back"
date: 2009-01-17
forum: General Help
---

### Post by jhefferon on 2009-01-17
Hello,

I'm trying to transfer files from an old server to a new one.  The new is Ubuntu 8.04.  The old is an older Debian.

I created a new user "jim".  I made the mistake of rsync-ing /home/jim from the old to the new.  Then when I logged in as jim, a lot of the configuration stuff was off-- icons didn't display, that kind of stuff.  

I realized my mistake and decided to delete the user, drop the directory, and then re-create the user (and to be more selective in copying over data).

So as a non-jim administrative user I used the administrative form to drp the user, deleted the directory (and killed a couple of processes), and then reopened the form and created the user again.  

Now when I log in as jim nothing works.  I am ssh-ing in and calling gnome-session, and I get perhaps a dozen error message boxes.  A typical one is that I cannot connect to the configuration server, but there are a number.  The screen is black (except for the one terminal) so the regular gnome window icons, the panels, etc., are not appearing.

Any suggestions?  I'd be very grateful.

Jim

---

### Post by yoyoned on 2009-01-17
What tools are you using to add/drop users?

---

