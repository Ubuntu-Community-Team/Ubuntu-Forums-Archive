---
title: "Adding New Users"
date: 2009-01-04
forum: General Help
---

### Post by coladons on 2009-01-04
Just installed 8.10 and at installation time, created one user account.  I am now ready to create additional users but the administration tool (Users and Groups) does not prompt for the admin password and I cannot add any users.  Any clues?

Steve

---

### Post by x22 on 2009-01-04
try "sudo useradd <username>" in a terminal

---

### Post by Peter09 on 2009-01-04
If you are an Admin user you should have an UNLOCK button on the bottom of the GUI.

---

### Post by coladons on 2009-01-04
Thanks both of you.  It was the "unlock" button that got me confused.  I had to unlock my own account in order to do anything in the GUI.

I did run "sudo useradd uname" and that added the user.  When I brought up the admin GUI, the new user was there.  After I unlocked my own account, I was able to add the properties for the user and set the password.

Again, thanks.

Steve

---

