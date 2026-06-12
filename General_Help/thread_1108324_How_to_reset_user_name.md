---
title: "How to reset user name"
date: 2009-03-27
forum: General Help
---

### Post by xg7 on 2009-03-27
Please help.  My username is longer than I'd like it to be.  If I could have done auto-login without encountering a glitch it would be no problem. Thing is, when I enable auto-login I am propted for the network password key (for the secure wifi connection I am using) everytime.  I'm using Ibex.

Thanks

---

### Post by Iowan on 2009-03-27
Resetting a user name is possible, but probably more involved than you'd want to pursue.  Besides changing username in /etc/passwd and /etc/shadow, the home directory and ownership of all files would need to be edited.  Might be easier to build a new user, but getting files moved, giving new user **sudo** privileges, etc. wouldn't be trivial, either.

---

### Post by James_Lochhead on 2009-03-27
I recommend just adding a user (System > Admin > Users and Groups) then transfering all data from your original home to the new one. You would do that just by pressing alt+f2 and then typing gksudo nautilus and using the file manager.

---

### Post by coffeecat on 2009-03-27
> **James_Lochhead said:**
> I recommend just adding a user (System > Admin > Users and Groups) then transfering all data from your original home to the new one. You would do that just by pressing alt+f2 and then typing gksudo nautilus and using the file manager.

You'd have to do one more thing. The UID will be different so you'll have to 'sudo chown' everything to the new user. As **Iowan** said, this won't be a trivial task.

---

### Post by xg7 on 2009-03-27
Bummer, to bad I can't do auto-login.  What about that strange glitch with me being prompted for my wifi security code only when using auto-login (otherwise it retains the password and will connect automatically).

---

