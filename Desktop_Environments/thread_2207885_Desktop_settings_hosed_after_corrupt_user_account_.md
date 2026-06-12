---
title: "Desktop settings hosed after corrupt user account restored"
date: 2014-02-25
forum: Desktop Environments
---

### Post by timcallagy on 2014-02-25
My user account became corrupted recently. 
To fix the issue, I basically had to create a new user, move /home/old_user to /home/new_user and set ownership of all files to new_user.

Most things are back to normal, but there are a few issues that are still present:
- can't change desktop background,
- can't add apps to unity launcher,
- can't add a new keyboard layout, 
- etc...

I'm guessing that the desktop settings files of old_user cannot simply be used for new_user. Anybody know what settings files I should be looking at for the kind of problems listed above?

Thanks,
Tim

---

### Post by r.stiltskin on 2014-02-25
Good guess.  If you take the corrupted desktop settings from old_user and give them to new_user, new_user now has corrupted settings and his desktop will be messed up too.

Create another new user and copy only the data files (not the hidden files) from old_user.  That way new user starts off with a clean slate & can do any customizations that you like.

---

### Post by timcallagy on 2014-02-26
Ya, I guess that's what I'm going to end up doing. Thanks

---

