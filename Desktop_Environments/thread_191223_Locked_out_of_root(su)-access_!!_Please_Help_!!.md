---
title: "Locked out of root(su)-access !! Please Help !!"
date: 2006-06-07
forum: Desktop Environments
---

### Post by SynapseR on 2006-06-07
I'm running Dapper.
I created a new user, then deleted it (the window informed me that the home dir would not be deleted, just login access).
I rebooted, logged in as my normal user and now I don't have SU/SUDO access :(
What do I do ???!?
There must be some config file I can edit in recovery mode ?

HELP ! HELP !

:)

---

### Post by tseliot on 2006-06-07
Boot in Recovery Mode.

Then type:
visudo

Look for this part:
```
# User privilege specification
root    ALL=(ALL) ALL
```

and add your username below root like in the following example:
```
# User privilege specification
root    ALL=(ALL) ALL
[COLOR="Red"]your_user_name ALL=(ALL) ALL[/COLOR]
```

Of course replace "your_user_name" with your username

CTRL+O to save, CTRL+X to exit

Then type:
```
reboot
```

---

### Post by nkhansen on 2006-06-07
You have to make sure that your user is in the admin group.
```
# adduser user admin
```

/etc/sudoers is a config file to edit, but this should be done with caution and the file should be backed up
```
# cp /etc/sudoers /etc/sudoers.orig
```

---

### Post by SynapseR on 2006-06-07
I used both suggestions and they worked perfectly.
Thank you sooo much !!!  :)

Any idea why I would have lost admin/root access in the first place ?

---

