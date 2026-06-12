---
title: "KDE su refuses password..."
date: 2005-10-27
forum: Desktop Environments
---

### Post by jyhelle on 2005-10-27
I did a fresh Kubuntu installation - in fact three successive installs the same day with full partition format each time :rolleyes: 
Everything goes OK, except that after post-installation and login, when I try any admin level menu item (adept, KUser, etc) the password is rejected as incorrect for the first two tries, then "impossible to communicate with su" until next reboot (logging out then back in isn't sufficient) 
When installing, I said yes to password shadowing, I gave a root pwd and created a user account with another password. 
The password I give to the KDEsu prompt is the user one (I also tried the root one, but to no avail) 
If I open a console and issue an "su" command with the root password, I become root so it seems su itself is OK 

edit: platform is AMD-64, Kubuntu version 5.10, DVD version downloaded over the net...

any idea ? 
JL

---

### Post by shakin on 2005-10-27
First, does regular sudo work from the command line? If it does, try removing kdesu (including config) and then reinstalling. Also try gksudo instead. If sudo from the command line doesn't work, continue...

As root, run 'cat /etc/sudoers'. Make sure these two lines are in there and uncommented:
```

root    ALL=(ALL) ALL
%admin  ALL=(ALL) ALL

```

Now run 'cat /etc/group |grep admin'. Two lines are displayed, beginning with lpadmin and admin. On the admin line make sure your username is at the end. Separate multiple sudo users with a comma.
```

admin:x:109:jsmith,jseinfeld

```

If that's all there then you should be able to use sudo, including kdesu.

---

### Post by jyhelle on 2005-10-27
thanks for the speedy reply !

the root entry appeared in the /etc/sudoers file, but not the %admin one, so I used visudo to add it

next the /etc/group file: no admin line, only the lpadmin one
I looked at a complete cat of the file, there is an "adm" group entry with my name at end, but no "admin" (number 109 here is the "messagebus" entry)

should I add an admin group ?

(that will be tomorrow anyway, since it's 00:15 by now, I'll get some rest :smile: )

cheers,
JL

---

### Post by Takis on 2005-10-27
You should be in both 'adm' and 'admin'.

---

### Post by jyhelle on 2005-10-28
OK, I added the missing admin group and all seems perfect.

Is there some logfile or such that I should keep to help someone investigate why this group was not created by the installation procedure ?

thanks for your help
JL

---

