---
title: "Add user in User Accounts not displaying /etc/passwd users"
date: 2014-08-11
forum: Desktop Environments
---

### Post by larzeb on 2014-08-11
I have created a new user and group from the cli. I needed to create the new user and group with specific IDs. They both show up in /etc/passwd and /etc/group.

However, this user is not available to add in the Unity User Accounts gui. In fact, the drop-down is disabled. 

How can I enable this user to login to the gui?

---

### Post by grahammechanical on 2014-08-11
You could have done this through User Accounts but we need to Unlock the utility and enter our administrator password.  I am assuming that you are using 14.04. There should be a button that says Unlock.

---

### Post by steeldriver on 2014-08-11
What uid, specifically? is it less than the default lightdm minimum-uid?

---

### Post by larzeb on 2014-08-11
Yes, I did unlock the the utility.

816 is the UID and GID. What is the minimum?

---

### Post by steeldriver on 2014-08-11
I'm not sure what you mean by the Unity User Accounts gui, but afaik the default minimum-uid to get the account to display in the lightdm greeter GUI is 1000

In 12.04, the setting is in /etc/lightdm/users.conf however I think it may have moved to somewhere in a conf.d/ directory in 14.04 - sorry I don't know for sure

```

[UserAccounts]
minimum-uid=500

```

---

### Post by Elfy on 2014-08-11
> /etc/lightdm/users.confStill the same in 14.04 and 14.10 for Xubuntu, I'd assume the same elsewhere

---

### Post by larzeb on 2014-08-11
The minimum is already set to 500 in /etc/lightdm/users.conf.

> [UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin




---

### Post by larzeb on 2014-08-11
I noticed [another post]("http://askubuntu.com/questions/139412/enabling-a-user-created-with-adduser-command-for-lightdm-graphical-login") pertinent to my problem. See the response by Sebastian Tylkowski.

I changed both the UID_MIN AND GID_MIN to 500 (both defaulted to 1000) in /etc/login.defs and my user showed up!

---

