---
title: "Trying to add a user"
date: 2009-05-21
forum: General Help
---

### Post by GnubbyaBush on 2009-05-21
Hi all my current user account doesn't have root permisions. I can't add a user, nor can I even adjust the group settings of my current default user or do anything with the root user (everything is greyed out.) I know I can change the password of the root then log in, but i don't want to do that. how do i figure out the random assigned password of the root, or basically how do i give my default user the permission to add users? or maybe like a run as admin (root) option for the user and groups feature.

---

### Post by R Clemons on 2009-05-21
It's best to not use a root user.  If your user is the one you created when you installed type
      sudo *command*
and enter your password

if you're trying to just add a user go to System->Administration->Users and Groups  click unlock select your user and enter your password

---

### Post by GnubbyaBush on 2009-05-21
thanks a ton

---

