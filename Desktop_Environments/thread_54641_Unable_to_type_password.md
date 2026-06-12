---
title: "Unable to type password"
date: 2005-08-05
forum: Desktop Environments
---

### Post by Event Horizon on 2005-08-05
I did a fresh install of kubuntu yesterday and I need to set the root password. However, after I type "sudo passwd root" into the konsole, it askes me for a password, but I can't type anything. It's like my keyboard entries are ignored.  ](*,) Anybody ever hear of this? Or what I could do?

EDIT: This happens any time it askes for a password. I can't use the konsole to edit my own password either!

---

### Post by DJ_Max on 2005-08-05
[QUOTE=Event Horizon]I did a fresh install of kubuntu yesterday and I need to set the root password. However, after I type "sudo passwd root" into the konsole, it askes me for a password, but I can't type anything. It's like my keyboard entries are ignored.  ](*,) Anybody ever hear of this? Or what I could do?

EDIT: This happens any time it askes for a password. I can't use the konsole to edit my own password either![/QUOTE]
 When typing passwords in the terminal, it won't show you typing anything.

---

### Post by Event Horizon on 2005-08-05
God I'm stupid. Ok thanks! But now when I try to login as root it says

 "Root logins are not allowed!"

How do I fix this?

---

### Post by DJ_Max on 2005-08-05
Be sure to have follwed the instructions correctly for creation of a root account.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> Enabling the root account

Note: This is not recommended!

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root 

---

### Post by Event Horizon on 2005-08-05
No, that doesn't work. Is there a dialouge or configuration that I need to change to allow root to login?

---

### Post by varunus on 2005-08-05
I would highly recommend not using the root account unless you have to.  If you log in as a user, "sudo commandname" will run it as root.  You can use the super user file browser, and you can also type sudo -s in a console to get a root terminal.

Its safer security wise to have no root account, since then, any hacker has to guess/know your username...there's no root account that they know exists.

In GNOME, you have to go to the login manager properties to enable root to login graphically.  It might be the same in KDE, check the control center's login manager section.

---

### Post by Event Horizon on 2005-08-05
but I need to edit my "fstab" and only root has the write permission. I have no clue how to do it without logging in as root. And the login manager is all greyed out (can't be changed). And the only options in there is the order they appear in and their display picture.

---

### Post by DJ_Max on 2005-08-05
[QUOTE=Event Horizon]but I need to edit my "fstab" and only root has the write permission. I have no clue how to do it without logging in as root. And the login manager is all greyed out (can't be changed). And the only options in there is the order they appear in and their display picture.[/QUOTE]
 ```
sudo nano /etc/fstab
```
Enter the password of your orginal account.

You DO NOT have to be root, you just need proper permissions. Read the article I provided in my reply.

---

