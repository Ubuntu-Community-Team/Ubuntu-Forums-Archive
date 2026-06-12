---
title: "Allowing an admin to log into any account?"
date: 2006-05-26
forum: Desktop Environments
---

### Post by mikeycooper on 2006-05-26
I'm setting up a PC for a mom with several children.  The mom has an admin-priv'd account and each child's user-priv'd account has a password so the kids cannot touch each other's stuff.  I'd like to give the mom a way to log in to the children's accounts from hers without having to remember their passwords.  Is there any way to allow this functionality through breezy (or even dapper, for that matter)?

Thanks for any help!
Mikey

---

### Post by halfvolle melk on 2006-05-26
If mom's a sudoer she can switch to any user like this:
```
sudo su [username]
```
I don't know how this could be done for GUI stuff/without terminal.

---

### Post by Ramses de Norre on 2006-05-26
```
sudo su username && nautilus
```
will give her nautilus running as the user she specified, she can then browse the home folder. She can start any application from that terminal as the specified user too. But since everything outside the home folder is general system config, I guess the home folder will be what she'll want to acces.

---

### Post by mikeycooper on 2006-05-26
I'm guessing she'll want to use it more to keep an eye on internet usage (looking at recent history in epiphany or firefox, for example).

Is there a way to bring up an entire gnome desktop instead of nautilus?  If it were contained in a separate window like in the case of the Remote Desktop app for logging into a win32 box, that would be ideal.  Not sure if that's technically feasible, but I don't think she'd be comfortable/knowledgeable enough with a terminal or poking through the . directories in nautilus).

---

