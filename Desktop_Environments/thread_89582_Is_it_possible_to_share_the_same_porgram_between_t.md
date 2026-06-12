---
title: "Is it possible to share the same porgram between two users?"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-12
I have two different log-ins and wanted to know if it is possible to access the same thunderbird program from either log-in?

---

### Post by adwait on 2005-11-12
Well, if you coped the ~/.mozilla-thunderbird directory into the other users home directory, he would have the same accounts and mails (that were there before). But after that, if you download mail with one account you won't see it in the other account. An alternative to this would be to run thunderbird as the same user in both the accounts. To run a program as a different user, open terminal and type
```
su <username> <program name
```

---

### Post by popeye on 2005-11-13
Hello,

I am still working on this but so far i worked it out like this:

Copy/move the profile folder to /var/mail/Profile.....

Change the owner and group of that folder to mail with

```
sudo chown -R mail:mail /var/mail/Profile.....
```

Change permissions to owner and group read/write with:

```
sudo chmod -R 770 /var/mail/Profile.......
```

Then add your user to the group mail with:

```
sudo adduser "youruser" mail
```

point the path in /home/youruser/.mozilla-thunderbird/profiles.ini to /var/mail/Profile....

and it should run. (change the dots with your profile name)

In theory this should work, but i am still trying and get strange errors in my mail so if someone has a better solution i'm looking forward to it.

---

### Post by steve.horsley on 2005-11-13
How about this:

Create a group tbshare and put both users in that group. Menu / System / Administration / Users and Groups

In the home directory of user1, change the group ownership of .thunderbirdto tbshare:
$ **chgrp -R tbshare .thunderbird**

In the home directory of users2:
Delete the .thunderbird folder :
$ **mv .thunderbird .thunderbird-original**

Link .thunderbird to the shared folder in user1's home:
$ ln -s ../user1/.thunderbird .thunderbird

This is untried, but I think it should work.
I advise that you back up user1's .thunderbird folder first though.

Steve

---

### Post by popeye on 2005-11-13
Hello again.

Worked it out. I think i solved the problem.

When opening thunderbird it reads ....../Profiles/abcd.default/prefs.js
so this file needs to be readable.

When thunderbird closes it changes the permissions of prefs.js to owner rwx, group rx, world --- and the owner and group are set to the current user. So this means when the other user try's to open thunderbird, this file is not readable to him, because he is no owner and even if he would be member of the group he has also no write permission. The file will be replaced after closing so your email is wrecked.

A solution for this is to start it with a script wich changes rights and ownership of this file after closing down thunderbird. (To be done after closing because then you are owner of the file so you can change these things)

make this script in /var/mail or whatever your profile location is.

> #! /bin/bash
#/var/mail/thunderbirdhack   
#start emailprogram mozilla-thunderbird
/usr/bin/mozilla-thunderbird
#after closing of program the following lines will be executed
#change permissions of prefs.js to group rw an owner rw
chmod 770 /var/mail/b4uqsucy.default/prefs.js
chown :mail /var/mail/b4uqsucy.default/prefs.js


make the file executable and start thunderbird with this script.

Things should work then.

---

